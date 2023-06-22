---
title:  "[Python] 파일입출력 기본"
excerpt: "Python 파일입출력 기본"

categories:
  - Python
tags:
  - Python
last_modified_at: 2023-06-22
---


# Python - 파일입출력 기본

### 파일 입출력의 기본

- `파일로부터 데이터를 읽어와서` 프로그램에 사용하기 위해
- `프로그램에서 만든 데이터`를 파일형태로 저장하기 위해

### 파일 열기 모드

- w : 쓰기 모드(write)
- a : 추가 모드(append)
- r : 읽기 모드(read)

<aside>
💡 작업 순서는 **`파일 열기 → 파일 작업 → 파일 닫기`** 순서로 진행 된다.

</aside>

```python
파일객체 = open(”파일이름”, “파일모드”)

파일객체.wrtie(데이터)

파일객체.close()

file = open("data.txt", "w")
file = open("data.txt", "a")
# 둘의 차이는 w는 덮어쓰기, a는 이어쓰기라고 생각하면 이해가 쉽다.

file = open("data.txt", "w") # 파일 열기
# open 함수를 이용해 data.txt를 객체형태로 가져와서 file이라는 변수에 담아둔다.

file.write("1. 파이썬 공부") # 파일 작업
# 문자열을 파일 객체에 쓰게되고 data.txt에 데이터로 들어가게 된다.

file.close() # 파일 닫기
# 열었던 파일을 닫아준다.

# 파일 읽기 모드
file = open("data.txt", "r") # 파일 읽기모드로 열기

data = file.read()
# 파일 객체의 read() 함수를 이용하면 data.txt에 있는 데이터 전체를 가져온다.

file.close()
# 열었던 파일을 닫아준다.
```

### 실습

Visual Studio Code를 이용해 실습해보자

### 1. 파일 쓰기

![Untitled](https://github.com/wktls63/wktls63.github.io/assets/107481916/c88628e8-51a4-43f4-aaed-ee175d960ac9)


- file 이라는 변수에 open함수를 이용해 경로상의 data.txt 파일을 “w” 즉 쓰기모드로 실행한다.
    - 경로상에 data.txt 파일이 없으면 자동으로 생성된다.
    - encoding=”utf8”를 작성해 인코딩 방식을 설정해주면 vs code에서 data.txt파일 내용이 깨지지 않게 볼 수 있다.

![Untitled 1](https://github.com/wktls63/wktls63.github.io/assets/107481916/3e624e84-044d-498f-ac1c-19dab12dd5cf)

![Untitled 2](https://github.com/wktls63/wktls63.github.io/assets/107481916/b0cb5841-41ba-4e3d-a300-c48f525aa58b)

- data.txt 파일이 생성되었고, 내용이 추가 된 것을 확인 할 수 있다.

### 2. 파일 추가

![Untitled 3](https://github.com/wktls63/wktls63.github.io/assets/107481916/0a50bbc8-a35a-4474-a967-6585e10a1915)

- 위에서 w 모드는 덮어쓰기라 설명했다, a 모드는 이어쓰기 즉 기존에 data.txt파일에 있는 내용 뒤에 추가한 내용을 이어쓰기 하는거라 생각하면 된다.

![Untitled 4](https://github.com/wktls63/wktls63.github.io/assets/107481916/826c1b41-152d-48d2-aee0-d2e2b8a1df2e)

- 새로운 내용이 추가 된 것을 확인 할 수 있다.

### 3. 파일 읽기

![Untitled 5](https://github.com/wktls63/wktls63.github.io/assets/107481916/efa8b721-8fe9-4518-8d7f-f7084ad71edc)

- “r” 읽기모드로 불러온 파일 데이터를 read함수를 통해 data라는 변수값에 넣어주고 프린트로 출력해본다.

![Untitled 6](https://github.com/wktls63/wktls63.github.io/assets/107481916/361032f3-aed0-4952-8bf8-8e2834d3f7be)

data.txt 내용에 있는 데이터 값들이 터미널에 잘 출력되는 것을 확인 할 수 있다.

### 번외) 파일 한 줄 읽기

![Untitled 7](https://github.com/wktls63/wktls63.github.io/assets/107481916/863fcb5d-4fcb-462f-9765-4e918a49b69e)

- 파일안에 내용이 몇 줄인지 알수없다. while 반복문을 활용해보자
- file.readline()이라는 함수는 한 줄씩 읽게되는데 이런식이면 파일의 끝이 어디가 되는지 알 수 없다.
- 그래서 if문을 통해 data 를 한 줄씩 읽다가 공백으로만 이루어진 구간이 나오면 break를 통해 반복문을 멈추게 작성했다.