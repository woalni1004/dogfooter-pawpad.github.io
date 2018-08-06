---
layout: post
title: 2. PyAutoGui
---

이번 포스팅에서는 Python 라이브러리 PyAutoGui 를 사용해서 어떻게 마우스를 제어할 수 있는 지 좀 더 자세히 알아보겠습니다.

목표
=

* Pyautogui 라이브러리를 사용해서 마우스 제어(이동, 클릭, 드래그)하기 

준비물
=

* Microsoft Windows OS가 설치된 개인 컴퓨터. (Windows OS란 우리가 흔히 말하는 윈도우7, 윈도우8, 윈도우10입니다. 특별한 목적을 가지고 컴퓨터를 사용하는 분 외에는 대부분 윈도우가 설치되어 있을 것입니다.)

* PyAutoGui 라이브러리: pip install pyautogui 명령어로 설치 가능합니다.


PyAutoGui
=

이제 본격적으로 Python 코딩을 하면서 PyAutoGui 가 제공해주는 기능을 하나하나 살펴볼 것입니다. Python 코딩은 적당한 편집기를 사용해서 편집하면 됩니다. IDLE 을 사용해서 테스트 코드를 짜는 게 가장 좋은 방법일테지만 코드가 점점 길어질수록 자연스럽게 편집기(저는 에디터와 편집기라는 단어를 혼용해서 사용합니다.)를 사용하고 싶어질 겁니다. 저같은 경우에는 간단한 코드들은 IDLE 로 테스트를 하면서 "아 이런 기능을 하는군" 하면서 잘 동작하는 지를 확인하고, 실제 프로젝트에 코드를 반영 하고 있습니다. 제가 주로 쓰는 에디터는 [Sublime Text 3](https://www.sublimetext.com/3)이라는 것인데, 무료에다가 가볍고 자동 완성 기능이 잘 되서 좋습니다. (주기적으로 팝업창이 뜨긴하지만... 크게 거슬리진 않습니다.)

우선 PyAutoGui 라이브러를 사용하려면 다음과 같은 코드를 무조건 작성해야 합니다. 스크래치(아무것도 없는 빈 문서, 새 파일을 의미)에서 시작해봅니다.
(IDLE 을 사용해서 테스트하는 방법은 이전 포스팅에서 설명했기 때문에 지금부터는 에디터로 할 것입니다. IDLE 로 해도 무방합니다.)

아래와 같이 에디터에 입력을 해보세요.

```
import pyautogui
```

또는 IDLE 를 실행해서 아래와 같이 입력해보세요.

<br />

![Alt text](/images/python_2_0.PNG)

<br />

IDLE 로 테스트 중이라면 결과를 바로 확인할 수 있습니다. 위 예제처럼 아무런 일도 벌어지지 않았다면 성공한 것입니다.(보통 리눅스 스타일의 컴퓨터에서는 성공하면 조용하고 실패하면 시끄럽게 떠듭니다..)

```
Rule of Silence
Developers should design programs so that they do not print unnecessary output. This rule aims to allow other programs and developers to pick out the information they need from a program's output without having to parse verbosity.
```

[출처 : 위키피디아(유닉스 철학)](https://en.wikipedia.org/wiki/Unix_philosophy)

편집기로 입력한 경우라면 바로 결과를 확인할 수 없습니다. Python 에게 제가 방금 작성한 문서를 던져줘야 결과가 나옵니다. 먼저 방금 작성한 문서를 저장합니다. 저장하는 경로를 반드시 알고 있어야 합니다. 그래야 Python 에게 이 문서가 어디에 있는 지 알려줄 수가 있으니깐요. 아 그리고 저장할 때는 확장자를 가급적이면 .py 라고 붙여주세요. 아무거나 해도 되긴 하지만 "아 이 문서는 Python 프로그램이구나" 라고 사람들에게 알려주는 게 좋지 않겠습니까? 왠만하면 .py 라고 확장자를 만들고 저장해주세요. 저는 test_pyautogui.py 라고 저장했습니다.

저장을 완료했다면 cmd 창을 열어주세요. 윈도우 키를 누르고(또는 좌측 하단 윈도우 아이콘을 클릭) cmd 라고 입력하면 눈 앞에 검은색 작은 실행 아이콘(보통은 명령 프롬프트라고 써있습니다.)이 검색될 것이니 클릭하세요. 먼저 Python 이 잘 실행되는 지 체크해보세요. 아래와 같이 나왔다면 Python 이 잘 실행되는 것입니다. 만약 아래와 같은 입력란이 나오지 않고 에러라고 생각되는 메세지가 나왔다면 [0. How to install Python](https://dogfooter-master.github.io/How-to-install-Python/) 을 정독하시고 다음 단계로 넘어가시길 바랍니다.

<br />

![Alt text](/images/python_2_2.png)

<br />

Python 이 잘 있는지(?) 확인했다면 이제 Python 에게 방금 전에 저장한 문서를 던져 줍시다.(.py 라고 저장했다면 문서를 더블클릭해도 되긴합니다만 실행되고 바로 사라지기 때문에 일단은 제가 하는 방법대로 따라해주시길 바랍니다.) 우선 Ctrl+Z 키를 눌러서 python 명령어 입력창을 중지시키고 아래와 같이 입력해보세요. 그럼 결과를 확인할 수 있을 것입니다.
<br />

![Alt text](/images/python_2_3.png)

<br />

제가 작성한 코드는 C:\workspace 폴더에 저장했기 때문에 저런 입력을 한 것입니다. 각자 본인이 방금 작성한 문서를 어디에 저장했는 지에 따라서 입력되는 위치나 파일 경로가 달라진다는 것을 명심하세요. 무조건 저랑 같게 하실려면 C:\workspace 라는 폴더를 만들고 그 안에다 저장하시면 됩니다.





