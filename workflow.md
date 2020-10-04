# Hanyang Univ. ERICA Software Department </br>[Software Development Practice] Git workflow team project

### 0️⃣ 팀소개
-----
1. 이용현 (팀장 / 소프트웨어학부 / 2019034684)
2. 김문주 (소프트웨어학부 / 2019038277)
3. 김종언
4. 이승섭
5. 최진영 (소프트웨어학부 / 2019095905)
6. 황순태
-----  
### 1️⃣ 팀 워크플로우 개요 (Forking flow)
-----
1. 모든 프로젝트 참여자가 `개인적인 로컬 저장소`와 `공개된 자신의 원격 저장소(하나의 중앙 원격 저장소를 각자가 Fork한 것)`, 즉 `두 개씩의 Git 저장소`를 가지는 방식이다.  
2. 모든 코드 기여자가 하나의 `중앙 저장소에 푸시하는 것이 아니라, 각자 자신의 원격 저장소에 푸시`하고, `프로젝트 관리자만 다른 개발자들의 기여분을 중앙 원격 저장소에 병합할 수 있다`는 점이 가장 큰 특장점이다.  
  - 소규모의 팀에서는 팀원 모두가 프로젝트 관리자가 되어 중앙 원격 저장소를 관리할 수 있다.
3. `아주 큰 규모의 분산된 팀에서도 안전하게 협업하기에 좋은 협업 방법`이다.  
4. `오픈소스 프로젝트에서 많이 사용하는 방식`이다.  
-----  
### 2️⃣ Git 워크플로우 진행 방식 (Forking flow)
-----  
#### 1. 프로젝트 팀 전체가 사용하는 중앙 원격 repository, 개인이 사용하는 개인 원격 repository, 개인이 사용하는 개인 로컬 repository를 아래의 이미지와 같이 구성함.  
![Alt text](http://alldpublic.kr/SDP_Team/1.jpeg)  

#### 2. 중앙 원격 저장소를 포크(fork)해서 자신만의 원격 저장소를 만든다.  
  - 중앙 원격 저장소를 복제한 저장소는 개인의 공개 저장소(remote repository) 역할을 함.  
  - 다른 개발자는 자신의 원격 저장소에 푸시할 수 없음(내려 받는 것은 가능)  
![Alt text](http://alldpublic.kr/SDP_Team/2.jpeg)  

#### 3. 프로젝트 참여자는 git clone 명령으로 로컬 저장소를 만든다.
```
git clone [개인 원격 remote 저장소 주소]
```
![Alt text](http://alldpublic.kr/SDP_Team/3.jpeg) 

#### 4. 로컬 저장소와 중앙 원격 저장소, 개인 원격 저장소를 연결한다.
[로컬 저장소 - 중앙 원격 저장소 연결]  
```
$ git remote add center [중앙 원격 remote 저장소 주소]
```  
[로컬 저장소 - 개인 원격 저장소 연결]
```
$ git remote add origin [개인 원격 remote 저장소 주소]
```
![Alt text](http://alldpublic.kr/SDP_Team/4.jpeg) 

#### 5. 새로운 기능 개발을 위해 격리된 branch를 만든다.
```
$ git checkout -b [branch name]

# 위의 명령어는 아래의 두 명령어를 합한 것
$ git branch [branch name]
$ git checkout [branch name]
```
![Alt text](http://alldpublic.kr/SDP_Team/6.jpeg) 

#### 6. 로컬 저장소의 커밋 이력을 자신의 원격 저장소(remote repository)에 푸시한다.
```
$ git commit -a -m "Write commit message"

# 위의 명령어는 아래의 두 명령어를 합한 것
$ git add . # 변경된 모든 파일을 스테이징 영역에 추가
$ git add [some-file] # 스테이징 영역에 some-file 추가
$ git commit -m "Write commit message" # local 작업폴더에 history 하나를 쌓는 것
```  
![Alt text](http://alldpublic.kr/SDP_Team/7.jpeg) 

#### 7. 프로젝트 관리자(소규모 팀에서는 모두가 관리자가 될 수 있음)에게 자신의 기여분을 반영해 달라는 풀 리퀘스트를 던진다.
![Alt text](http://alldpublic.kr/SDP_Team/8.jpeg) 

#### 8. Pull requests를 merge 하기 위한 회의(코드리뷰)를 진행한다.
![Alt text](http://alldpublic.kr/SDP_Team/9.jpeg) 

#### 9. 회의 후 프로젝트 관리자는 merge를 진행한다.
![Alt text](http://alldpublic.kr/SDP_Team/10.jpeg) 

#### 10. 중앙 원격 저장소와 자신의 로컬 저장소를 동기화하기 위해 로컬 저장소의 branch를 master branch로 이동한다.
![Alt text](http://alldpublic.kr/SDP_Team/11.jpeg) 

#### 11. 중앙 원격 저장소의 코드 베이스에 새로운 커밋이 있다면 다음과 같이 가져온다.
```
$ git pull center master
```
![Alt text](http://alldpublic.kr/SDP_Team/12.jpeg) 
-----  
### 3️⃣ Forking workflow의 장단점
1. 장점  
  - 개인 원격 저장소에서 발생한 업데이트는 중앙 원격 저장소에 영향을 주지 않으므로, 다양한 시도를 하기에 좋다.
  - 어떤 기준에 따라 잘 분류되어 있는 프로젝트에 적용하기 좋다.
2. 단점
  - git을 처음 써보는 사람의 경우 workflow를 이해하기가 다른 flow보다 상대적으로 어렵다.
  - 작업 상황을 자주(짧은 주기로) 리뷰하기가 쉽지 않다. → 통일된 관리가 어렵다.
