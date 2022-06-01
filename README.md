# homework
# 목차
1) top 명령어 
2) ps 명령어
3) jobs 명령어
4) kill 명령어
5) 매크로 사용법

## top 명령어 = 실시간으로 CPU 사용률 체크를 해주는 도구

![제목 없음](https://user-images.githubusercontent.com/106470078/171462553-e793504d-cef0-4955-b02f-9cbe1e88a22e.png)
### 실행화면

**1번째줄** 


04:56:55 는 현재 서버의 시간


0 user : 현재 0명의 사용자 접속


load average : 부화율


**2번째줄**


total 5개의 프로세스 가동중


running 1개의 프로세스가 실행중


sleeping 4개의 프로세스 대기중


stopped 0개의 프로세스가 멈춤


zomie 0개의 프로세스가 좀비상태 
*좀비상태 프로그램이 종료되었음에도 메모리상에서 프로세스에 대한 정보가 사라지지 않은상태


**3번째줄** 


us 유저레벨에서 사용하고 있는 cpu 비중


sy 시스템 레벨에서 사용하고 있는 cpu비중


id 유휴 상태의 cpu 비중


wa 시스템이 i/o 요청을 처리하지 못한 상태에서의 cpu idle 상태인 비중


**4번째줄** 


mem 
total 12686.9 전체 물리적인 메모리


free 사용되지 않은 여유 메모리


used 사용중인 메모리


buff/cache 버퍼된 메모리


 **5번째줄**


swap


total 전체 스왑메모리


free 여유 스왑메모리


used 사용중인 스왑 메모리


availMem : 여유 물리메모리


PID : 프로세스 ID (PID)  


USER : 프로세스를 실행시킨 사용자 ID


PRI : 프로세스의 우선순위 (priority)


NI : NICE 값. 일의 nice value값이다. 마이너스를 가지는 nice value는 우선순위가 높음.


VIRT : 가상 메모리의 사용량(SWAP+RES)


RES : 현재 페이지가 상주하고 있는 크기(Resident Size)


SHR : 분할된 페이지, 프로세스에 의해 사용된 메모리를 나눈 메모리의 총합.


S : 프로세스의 상태 [ S(sleeping), R(running), W(swapped out process), Z(zombies) ]


%CPU : 프로세스가 사용하는 CPU의 사용률


%MEM : 프로세스가 사용하는 메모리의 사용률


COMMAND : 실행된 명령어


|옵션|설명|
|---|---|
| shift + p|CPU 사용률이 높은 프로세스 순서대로 표시|
| shift + m| 메모리 사용률이 높은 프로세스 순서대로 표시|
| shift + t|프로세스가 돌아가고 있는 시간 순서대로 표시|
|- k|프로세스  kill  - k 입력 후 종료할 PID 입력 signal을 입력하라고 하면 kill signal인 9를 입력|
| - a|메모리 사용량에 따라 정렬|
|- b|Batch 모드 작동|
|- c|명령행/프로그램 이름 토글|
|- d|지연 시간 간격은 다음과 같다. -d ss. tt (seconds.tenths)|
| - h |도움말 |
|- H|스레드 토글|
|- i|유휴 프로세스 토글|
|- m|VIRT/USED 토글|
|- M|메모리 유닛 탐지|
|- n|반복 횟수 제한 : -n number|
|- p|PID를 다음과 같이 모니터 : -pN1 -pN2 ... or -pN1, N2 [, ...] |
|- s|보안 모드 작동|
| - S|누적 시간 모드 토글|
|- u|사용자별 모니터링 : -u somebody|
|- U|사용자별 모니터링 : -U somebody|
|- v|version|
|space bar|refresh|
|- u|입력한 유저의 프로세스만 표시 - which u|
|숫자 1|CPU Core별로 사용량을 보여준다.|

----
## ps명령어 = 현재 실행중인 프로세스 목록을 보여주는 명령어

![ps 실행화면](https://user-images.githubusercontent.com/106470078/171464205-cc1073c7-9807-4763-b8b8-b965c8a59f7f.png)


### 실행화면

**ps 옵션**
|옵션|설명|
 |---|---|
|-e| 모든 프로세스를 출력해 준다.|
|-f| 풀 포맷으로 보여준다.(UID, PID 등)|
|-l| 긴 포맷으로 보여준다.|
|p, -p| 특정 PID의 프로세스를 보여준다.|
|-u|  특정 사용자의 프로세스를 보여준다.|


자주사용하는 명령어 "ps -ef | grep -" 원하는 프로세스만 추출

---
## jobs 명령어 = 백그라운드로 실행되는 작업목록(작업번호, 상태, 명령어)을 보여주는 리눅스 명령어


※ 사용법
jobs [옵션] [job ID]
jobs -x command [args]

 |옵션|설명|
|---|---|
|-l|프로세스 그룹 ID를 state 필드 앞에 출력|
|-n|프로세스 그룹 중에 대표 프로세스 ID를 출력|
|-p|각 프로세스 ID에 대해 한 행씩 출력|
|command|지정한 명령어를 실행|

※ jobs로 알 수 있는 세션의 상태 값

 |상태|설명|
|---|---|
| Running|작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중임|
 |Done|작업이 완료되어 0을 반환하고 종료 했음을 의미|
 |Done(code)|작업이 정삭적으로 완료되었으며, 0이 아닌 코드를 반환 했음을 의미|
 |Stopped|작업이 일시 중단|
|Stopped(SIGTSTP)|SIGTSTP 신호가 작업을 일시 중단|
 |Stopped(SIGSTOP)|SIGSTOP 신호가 작업을 일시 중단|
 |Stopped(SIGTTIN)|SIGTTIN 신호가 작업을 일시 중단|
|Stopped(SIGTTOU)|SIGTTOU 신호가 작업을 일시 중단|
---
## kill 명령어 = 프로세스에 특정한 signal을 보내는 명령어, 일반적으로 종료되지 않는 프로세스를 종료 시킬 때 많이 사용한다.


**※ 사용법**


$ kill [options] <pid> [...]

|시그널|설명|
|---|---|
|SIGHUP|	세션이 종료될 때 시스템이 내리는 시그널|
|SIGINT|Ctrl + C, 종료 요청 시그널|
|SIGKILL|강제 종료 시그널|
 |SIGSEGV|메모리 침범이 일어날 때 시스템이 보내는 시그널|
 |SIGTERM|기본 값, 종료 요청 시그널|
 |SIGTSTP	|Ctrl + Z 일시 중지 요청 시그널|
---
## 매크로 사용법
  
  
vi에서 매트로는 명령어 모드에서 
q + 알파벳을 눌러 특정 알파벳에 매크로를 저장

순서는
1. q + a       a키에 recording 시작
2. 반복을 위한 내가 원하는 동작
3. q             recoding 종료
4. @a          1회 실행 
or @@         방금 실행한 매크로 실행
or 10@a       매크로 10회 실행
  
 **매크로 사용예시1**
  
  ![매크로 사용예시](https://user-images.githubusercontent.com/106470078/171465940-6f507ff9-f7a6-457e-b82d-cba878318ea5.png)

사용예시는 저번 과제의 vimgolf 4번문제 풀이
  
  
  ####Gqa-O//<C-N> TODO<Esc>q@aZZ
  
  처음에 qa로 a에다가 저장 q로 종료하고 @a로 매크로 저장한거 다시 사용 
  
  
  **매크로 사용예시2**
  
  ![메크로 사용예시](https://user-images.githubusercontent.com/106470078/171467680-f17fc065-0a42-4553-bf78-1641c3650206.png)

  
 **숫자 증가 매크로**

1. 1 숫자 입력
2. 매크로 시작
3. 1 숫자를 복사해서 다음줄에 붙여넣기
4. 두번째줄 1에 커서를 올리고 Ctrl+a(숫자 증가)
5. 매크로 종료

ctrl + a (숫자 증가)
ctrl + x ( 숫자 감소)

  **숫자응용 매크로**
  
![매크로 응용](https://user-images.githubusercontent.com/106470078/171469126-23902179-e90c-4f50-a008-5414486a6854.png)

  
  
