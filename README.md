<img width="100%" src="https://user-images.githubusercontent.com/87955005/140437612-1aa7120d-fa46-4500-8f63-33a1761add78.png"/>

>  **용용랜드**는 자바 콘솔 기반의 놀이공원 예매 및 관리 시스템입니다. <br />
>  하루 평균 4시간으로 **총 48시간** 동안( 21.10.22 - 21.11.02 ) **5명**의 팀원이 개발했습니다.

<br />

# 📌 Table Of Contents
* [📖 Introduction](#-introduction)
* [🙋 My Role](#-my-role)
* [🔎 Detail](#-detail)
* [💡 Consideration](#-consideration)

<br />
<br />
<br />



# 📖 Introduction
### 1. 프로젝트 개요
* 이클립스 콘솔로 회원 가입부터 놀이공원 예매 Process를 구현
* 관리자 계정으로 놀이공원 전반에 대한 CURD 수행
<br />

### 2. 개발 환경
* Windows 10
* JAVA JDK 11.0.12
* Eclipse IDE for Enterprise Java Developers
<br />

### 3. 프로젝트 내용
![순서도](https://user-images.githubusercontent.com/87955005/143726017-da373787-944c-47f4-bb7f-031078f81145.png)
#### 3-1. 비회원
* 회원가입 및 로그인, ID/PW 찾기
* 당일 쾌적도 현황 확인
* 놀이공원 정보 조회

#### 3-2. 회원
* 회원 정보 수정 및 탈퇴
* 예매 및 예약 사항 조회
* 어트랙션 예약
* 티켓 예매
* 설문 조사

#### 3-3. 관리자
* 직원 및 회원 관리
* 놀이공원 정보 관리
* 당일 티켓 예매 현황
* 놀이공원 통계 확인


<br />
<br />
<br />

# 🙋 My Role
### 1. 메인 화면 및 쾌적도 현황 공유
![main3](https://user-images.githubusercontent.com/87955005/143378820-05b55153-beaa-4c98-992d-64a09eabe987.gif)

#### 1-1. 메인 화면
* 엔터를 누르면 메인에서 메뉴 화면으로 전환됩니다.
* 메뉴 번호를 입력해 원하는 페이지로 이동할 수 있습니다.
* 잘못된 입력의 경우 "다시 입력해주세요."가 출력됩니다.

#### 1-2. 쾌적도 현황 공유
* 당일 티켓 소지자 기준으로 500명 이상이면 쾌적, 미만이면 혼잡을 안내합니다.

<br />
<br />

### 2. 회원의 티켓 예매 
![reservation2](https://user-images.githubusercontent.com/87955005/143387010-ca28189e-12dd-4681-a586-56b2cbe83e66.gif)

#### 2-1. 예매 날짜 선택
* 예매 가능한 날짜는 당일부터 2주 후이며 달력 형태로 안내합니다.
* 안내한 날짜 외 입력시 "잘못된 날짜입니다."가 출력됩니다.
* B 입력시 회원 메뉴로 되돌아갑니다. 

#### 2-2. 티켓 예매
* 성인/청소년/어린이 매수를 각각 입력합니다.
* 제휴 카드 사용시 할인된 가격이 적용됩니다.
* 예매된 티켓은 My Page에서 확인 가능합니다.

<br />
<br />

### 3. 관리자의 회원 관리
![user](https://user-images.githubusercontent.com/87955005/143388417-5c70773e-4aee-469c-9501-a2daf5cad53c.gif)

#### 3-1. 회원 조회 및 관리
* 페이지 당 10명의 회원을 조회합니다.
* </> 입력으로 페이지를 이동할 수 있으며, 불가능한 경우 "이전/다음 페이지가 없습니다."가 출력됩니다.
* 원하는 기능의 번호를 입력해 수행할 수 있습니다.
* B 입력시 관리자 메뉴로 되돌아갑니다. 

#### 3-2. 회원 검색
* 이름 검색을 통해 특정 회원의 정보를 알 수 있습니다.
* 검색과 일치하는 회원이 없을 경우 "존재하지 않는 회원입니다."가 출력됩니다.

#### 3-3. 회원 삭제
* 회원 고유 번호를 통해 회원을 삭제할 수 있습니다.
* 안내 메시지가 뜨며 Y 입력시 삭제가 정상적으로 진행됩니다.
* 삭제된 회원은 조회가 불가능합니다.

<br />
<br />

### 4. 관리자의 직원 관리
![employee](https://user-images.githubusercontent.com/87955005/143580150-94811eff-a822-4ce9-a077-b76e30528933.gif)

#### 4-1. 직원 조회/검색/삭제
* 회원 관리와 동일합니다. 

#### 4-2. 직원 추가
* 직원 정보 입력시 자동으로 고유 번호를 부가하며, 직원 데이터에 추가됩니다.
* 추가된 직원은 검색을 통해 조회 가능합니다.

#### 4-3. 직원 근무지 배치 및 수정
* 직원 번호를 통해 근무지를 배치합니다.
* 변경된 근무지는 직원 데이터에 반영해 조회할 수 있습니다.


<br />
<br />
<br />

# 🔎 Detail
### 1. 쾌적도 현황 공유
* 오늘 날짜를 티켓 테이블 칼럼의 유형에 맞게 String 변수에 초기화합니다.
    ```java
    Calendar c = Calendar.getInstance();
    String today = String.format("%tF", c).replace("-", "");
    ```
* Stream을 사용해 오늘 날짜와 일치하는 티켓 수를 구하고 현황을 반환합니다.
    ```java
    list.stream()
      .filter(r -> r.getDate().equals(today))
      .forEach(r -> total += Integer.parseInt(r.getAdultCount())
        + Integer.parseInt(r.getYouthCount())
        + Integer.parseInt(r.getKidCount()));
    return total < 500 ? "쾌적" : "혼잡";
    ```
<br />

### 2. 캘린더
* 해당 월의 1일이 무슨 요일인지 반환하는 메소드입니다.
    ```java
    int day = 0;
		for(int i=1; i<year; i++) {
			day += isLeapYear(i) ? 366 : 365;
		}
		for(int i=1; i<month; i++) {
			day += getLastDay(year, i);
		}
		day++;
		return day % 7;
    ```
* 해당 월의 마지막일을 반환하는 메소드입니다.
    ```java
    switch (month) {
		case 1, 3, 5, 7, 8, 10, 12 :
			return 31;
		case 4, 6, 9, 11 :
			return 30;
		case 2 : 
			return isLeapYear(year) ? 29 : 28;
		}
		return 0;
    ```
* 해당 해가 윤년인지 boolean값으로 반환합니다.
    ```java
		if(year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
			return true;
		} else {
			return false;
		}
    ```
<br />

### 3. 페이징
* 한 페이지당 10명의 직원만 조회하기 위한 for문 입니다.
    ```java
    for(int i=page*10; i<page*10+10&&i<list.size(); i++) {
			if(list.get(i).getSeq().equals("")) {
				break;
			}
			System.out.printf("\t\t\t\t\t %s%6s%6s\t%-25s\t%-13s\t%s%n"
							, list.get(i).getSeq()
							, list.get(i).getName()
							, list.get(i).getAge()
							, list.get(i).getAddress()
							, list.get(i).getPhoneNum().substring(0,3) + "-" 
								+ list.get(i).getPhoneNum().substring(3,7) + "-" 
								+ list.get(i).getPhoneNum().substring(7)
							, list.get(i).getWorkPlace());
		}
    ```
* 현재 페이지를 안내하는 페이지바를 출력합니다.
    ```java
    System.out.printf("\t\t\t\t\t< 이전페이지\t\t\t\t     %d / %d\t\t\t\t   다음 페이지 >%n", page+1, list.size()/10+1);
    ```
* 마지막 페이지의 경우 페이지 이동이 불가능하도록 if문을 사용했습니다.
    ```java
		if(page != list.size()/10) {
      page++;
    } else {
      System.out.println("\t\t\t\t\t\t\t\t다음 페이지가 없습니다.");
      return;
    }
    ```
<br />
<br />
<br />

# 💡 Consideration
### 1. 후기
> &nbsp;&nbsp;처음 투성이라 아쉬운 부분도 있지만, 개발이 더욱 좋아지게 만든 프로젝트였습니다. </br>
> &nbsp;&nbsp;팀원들과 Github으로 협업을 진행하며 초반에 많은 오류들이 발생했습니다. 가장 큰 문제는, 모두가 master로 커밋을 진행한 것입니다. 이후 각자 브랜치를 생성해 코드를 관리하며 충돌을 줄였습니다. 단순히 팀원 별로 브랜치만 나눈 것이라, 적합한 사용법은 아닙니다. 다음 프로젝트 시작 전 제대로 공부를 할 예정입니다.</br>
> &nbsp;&nbsp;하루에 30분씩이라도 서로의 코드를 보며 리뷰하는 시간을 가졌습니다. 덕분에 각자의 진행 사항을 체크하기 수월했고, 통합에도 큰 어려움이 없었습니다.</br>
> &nbsp;&nbsp;데이터 설계 당시 회원이 삭제될 경우를 고려하지 않아, 회원을 삭제할 경우 관련된 데이터들이 오류가 발생했습니다. 데이터 설계의 중요성에 대해 깊게 생각해볼 수 있는 계기가 되었고, 앞으로 프로젝트에서 같은 실수를 하지 않도록 주의할 것입니다.
<br />

  
