##### 주요 T-CODE의 종류와 기능

- SE09(SE10) 
  - TRANSPORT ORGANIZER
  - 개발 환경에서 개발된 객체들을 운영환경으로 이관 요청
- SE11
  - ABAP DICTIONARY
  - 테이블, 데이터타입, 도메인 조회 생성 수정 삭제
- SE37
  - FUNCTION BUILDER
  - FUNCTION을 생성하거나 조회 삭제
- SE80
  - OBJECT NAVIGATOR
  - ABAP의 객체를 조회하거나 생성 삭제
- /n
  - 초기화면으로 이동
- /h
  - 디버깅 모드로 프로그램 실행
- /o
  - 새로운 세션 생성



##### 프로그램 네이밍룰

Z 또는 Y로 시작해야 한다.



- MODULE POOL 프로그램
  - SAPMZ + MODULE(2) +SERIAL NUMBER
  - 비즈니스 플로우를 처리하는 유용한 개발환경을 제공한다.
  - SCREEN OBJECT를 중심으로 처리하고자 한느 요소들을 자유롭게 배치할 수 있으며 화면과 화면 사이의 로직을 구성해 프로그램을 만들 수 있다.
- REPORT 프로그램
  - Z + MODULE(2) + CATEGORY(1) + SERIAL NUMBER
  - REPORT 프로그램은 기본적으로 검색조건을 입력받고, DB에서 원하는 데이터를 추출해 가공한 뒤 결과값을 보여주는 프로그램이라고 생각하면 된다.

- CTS (CHANGE AND TRANSPORT SYSTEM)
  - 형상관리 툴
  - 개발 서버에서 생성/변경된 사항을 품질/운영 서버에 반영하는 도구이다.
  - 레포지토리(프로그램, 테이블 등)의 버전을 관리한다.



##### 단축키

- F1
  - 해당 구문에 대한 상세 문법을 확인할 수 있다.
- F4
  - 입력 필드에 커서를 놓고 F4를 누르면 해당 입력 필드에 대한 POSSIBLE ENTRY를 확인할 수 있다.



##### ABAP DICTIONARY

- DATA TABLE / VIEW / 데이터유형 / TYPE GROUP / SEARCH HELP / LOCK OBJECT가 있다.

- 오브젝트들의 정보를 METADATA 또는  DATA DEFINITION이라 정의하며, DATA DEFINITION을 정의하고 관리하는 역할을 ABAP DICTIONARY 가 하게 된다.
- 동적으로 ABAP WORKBENCH와 연결되어 있기 때문에 오브젝트의 변경은 각각의 ABAP PROGRAM과 SCREEN에 즉기 영향을 미친다.
- ABAP DICTIONARY는 시스템에서 사용되는 모든 데이터들을 중앙집중적으로 관리하기 때문에 무결성, 일관성, 안정성이 보장된다.

1. TYPE DEFINITION

- DATA ELEMENTS
- STUCTURES
- TABLE TYPES

2. DATABASE OBJECT

- TABLE
- VIEW



##### TABLE 조회 및 생성 (SE11)

- DELIVERY CLASS 의 종류
  - A
    - 보통 사용하는 CLASS로 MASTER DATA나 TRANSACTION DATA 저장 시 사용
  - C
    - 사용자에 의해 유지 관리되는 TABLE
  - L
    - 임시 데이터 저장용 테이블
  - G
    - 기존 데이터의 수정 및 삭제가 되지 않고 신규로 INSERT 되는 TABLE
  - E
    - SAP과 고객은 각자의 KEY 영역을 가지고 있는 컨트롤 테이블
  - S
    - 프로그램 변경 시 상태 정보를 가지고 있음
  - W
    - 데이터 전송 시 자신의 전공 객체를 가지고 전송됨



- 데이타 클래스
  - 테이블 성격에 맞게 알맞은 용도를 선택해 사용한다
- 크기범주
  - 테이블의 초기 데이터량을 설정
- 버퍼링
  - 일반적으로 버퍼링 허용 금지로 체크
  - 시스템의 메모리 상황을 잘 모르는 상태에서 모든 테이블에서 버퍼링을 사용한다면 시스템에 무리를 줄 수 있다.



##### 구조체

- 테이블과 동일한 형태지만 실제 DB 상에 존재하지 않는 객체로서, ABAP DIC에만 존재하며 DATA SET을 지니지 못한다.
- 다른 구조체나 프로그램에서 변수 선언시 참조로 사용되거나 테이블 또는 다른 구조 상에서 INCLUDE하여 재사용 가능하다.



##### VIEW

- 이미 존재하는 하나 혹은 그 이상의 테이블을 조인하여 가상으로 구성한 테이블.



##### DATA TYPE

- DATA TYPE

  - 프로그램에서 사용할 수 있는 데이터 타입을 정의

    ```ABAP
    TYPES dtype [TYPE type or LIKE dobj]
    ```

    

- DATA VARIABLE

  - DATA TYPE을 참조하여 값을 저장할 수 있는 변수

  ```ABAP
  DATA var [TYPE type or LIKE dobj]
  ```





##### DATA TYPE의 종류

- PREDEFIEND ABAP TYPE
  - 미리 선언된 타입
- ABAP DICTIONARY TYPE
  - 모든 ABAP 프로그램에서 사용할 수 있는 GLOBAL DATA TYPE
- LOCAL TYPE
  - 개별 프로그램 내에서 정의



##### PREDEFIENED ABAP DATA

- NUMERIC TYPE
  - I
    - 정수
  - F
    - FLOATING POINT NUMBER
  - P
    - PACKED NUMBER (소수자리 허용)
- CHARACTER TYPE
  - C
    - 문자, 숫자, 특수문자
  - D
    - DATA FIELD(날짜)
  - N
    - 숫자를 C타입으로 표현 INTEGER 형태를 문자 타입으로 보여줌
  - T
    - TIME FIELD
- HEXADECIMAL TYPE
  - X
    - 16진법 필드
- STRING for character strings
  - STRING은 가변 길이를 가지는 DATA TYPE C와 유사



EX)

```ABAP
DATA LV_TEXT1(20) TYPE C. "20자리의 문자
DATA LV_TEXT2 TYPE STRING. "가변길이 문자
DATA LV_NUM1 TYPE I.
DATA LV_NUM2 TYPE P DECIMALS 2. "소수자릿수 2
DATA LV_NUM3 TYPE P DECIMALS 3. "소수자리수 3
DATA LV_NUM4 TYPE P. "소수자리수 없음
DATA LV_NUM5 TYPE F. "16진수

LV_TEXT1 = '숫자'.
LV_NUM1 = 100.
LV_TEXT2 = '은 INTEGER 타입입니다.'.
WRITE: LV_TEXT1, LV_NUM1, LV_TEXT2.

SKIP.

LV_TEXT1 = '숫자'.
LV_NUM2 = 4 / 3.
LV_TEXT2 = '은 PACKED NUMBER 타입입니다.'.
WRITE: LV_TEXT1, LV_NUM2, LV_TEXT2.

SKIP.
SKIP.

LV_TEXT1 = '숫자'.
LV_NUM3  = 4 / 3.
LV_TEXT2 = '은 Packed Number 타입입니다.'.
WRITE: LV_TEXT1, LV_NUM3, LV_TEXT2.

SKIP.

LV_TEXT1 = '숫자'.
LV_NUM4  = 4 / 3.
LV_TEXT2 = '은 Packed Number 타입입니다.'.
WRITE: LV_TEXT1, LV_NUM4, LV_TEXT2.

SKIP.

LV_TEXT1 = '숫자'.
LV_NUM5  = 4 / 3.
LV_TEXT2 = '은 float 타입입니다.'.
WRITE: LV_TEXT1, LV_NUM5, LV_TEXT2.
```



EX)

```ABAP

DATA LV_DATE TYPE D.

LV_DATE = '20210825'.
LV_DATE+4 = '0216'. " 4자리 이후 값 변경
WRITE / LV_DATE.

LV_DATE+4(2) = '01'. " 4자리 이후 2자리 값만 변경
 WRITE / LV_DATE.


 CLEAR LV_DATE.
 LV_DATE = SY-DATUM. " 시스템 날짜
 WRITE / LV_DATE.

 LV_DATE = LV_DATE - 1. " 어제 = 오늘 - 1
 WRITE / LV_DATE.
```



- DATA ELEMENT는 DOMAIN으 참조한다.
  - 정의된 도메인은 복수의 DATA ELEMENT에서 재사용될 수 있다.
- 테이블 필드는 DATA ELEMENT를 참조한다.
  - 정의된 DATA ELEMENT는 복수의 테이블 필드에서 재사용될 수 있다.
- DATABASE TABLE과 VIEW 전체를 참조하여 구조체 및 인터널 테이블을 선언할 수 있다.
- TABLE의 필드만을 참조하여 선언할 수 있다.



##### INTERNAL TABLE

- TABLE(TRANSPARENT TABLE)
  - 하드디스크에 물리적으로 존재
- INTERNAL TABLE
  - 메모리 영역에 생성.
  - 프로그램이 실행되고 있는 동안 존재하는 가상의 테이블
  - 특정 레코드의 테이블 데이터를 조회/입력/변경하고자 할 때에 WORK AREA를 함께 사용
  - ABAP에서 인터널테이블이란 DB에 접근하여 데이터를 조회하고, 조회한 데이터를 Local(메모리영역)에 담아두는 것이다.
- WORK AREA
  - 테이블의 레코드와 동일한 TYPE으로 선언된 변수
  - Work Area는 하나의 레코드만 가질 수 있다. 하나 이상의 레코드는 절대 가질 수 없다.
  - 어떠한 internal table에 레코드를 더하고자 할 때, 우리는 그 레코드를 직접 internal table에 삽입할 수 없다. 무조건 work area를 통해서 만 가능하다. 



 INTERNAL TABLE에는 HEADER와  BODY로 구성된 것과 BODY만으로 구성된 것이 있다.

HEADER는 INTERNAL TABLE을 가지고 어떠한 작업을 수행할 때 BODY의 내용을 HEADER로 옮겨서 작업하며, DATA를 저장할 때는 반대로 HEADER의 내용을 BODY로 옮김으로써 저장된다.

즉, HEADER는 INTERNAL TALBE의 DATA에 대해 어떠한 작업을 수행할 수 있는 공간인 것이다.

(HEADER = WORK AREA)



EX)

```ABAP
TYPES : BEGIN OF PERSON,
   NAME(5) TYPE C,
  AGE TYPE I,
  ADDRESS(10) TYPE C,
  PHONE TYPE I,
  END OF PERSON.
  
  DATA : LS_PERSON TYPE PERSON.
  DATA : LT_PERSON TYPE TABLE OF PERSON.
```

EX)

```ABAP
TYPES : BEGIN OF PERSON,
   NAME(5) TYPE C,
  AGE TYPE I,
  ADDRESS(10) TYPE C,
  PHONE TYPE I,
  END OF PERSON.
*
*  DATA : LS_PERSON TYPE PERSON.
*  DATA : LT_PERSON TYPE TABLE OF PERSON.
*
*  DATA : BEGIN OF LS_PERSON,
*    NAME(5) TYPE C,
*    AGE TYPE I,
*    ADDRESS(10) TYPE C,
*    PHONE TYPE I,
*    END OF LS_PERSON.
*
*
*   DATA : LT_PERSON LIKE TABLE OF LS_PERSON.
*    DATA: LT_PERSON_H LIKE TABLE OF LS_PERSON WITH HEADER LINE.
*
* DATA: LS_PERSON_A LIKE LS_PERSON.
*    DATA: LS_PERSON_B LIKE LINE OF LT_PERSON.


    DATA: BEGIN OF LS_PERSON.
      INCLUDE TYPE PERSON.
      DATA: SEX(1) TYPE C,
            END OF LS_PERSON.

 DATA: LT_PERSON LIKE TABLE OF LS_PERSON.
 DATA: LT_PERSON_H LIKE TABLE OF LS_PERSON WITH HEADER LINE.


CLEAR LT_PERSON[].
CLEAR LS_PERSON.
LS_PERSON-NAME = '김씨'.
LS_PERSON-AGE = '35'.
INSERT LS_PERSON INTO TABLE LT_PERSON.

CLEAR LS_PERSON.
LS_PERSON-NAME = '박씨'.
LS_PERSON-AGE = '45'.
INSERT LS_PERSON INTO TABLE LT_PERSON.

CLEAR LS_PERSON.
LS_PERSON-NAME = '유씨'.
LS_PERSON-AGE = '40'.
APPEND LS_PERSON TO LT_PERSON.

CLEAR LS_PERSON.
LOOP AT LT_PERSON INTO LS_PERSON WHERE AGE = '40'.
  LS_PERSON-AGE = '60'.
  MODIFY LT_PERSON FROM LS_PERSON TRANSPORTING AGE.
  ENDLOOP.
  
LOOP AT LT_PERSON INTO LS_PERSON.
  WRITE:/ LS_PERSON-NAME, LS_PERSON-AGE.
  ENDLOOP.
  
  
 CLEAR LS_PERSON.
  READ TABLE LT_PERSON INTO LS_PERSON WITH KEY AGE = '60'.
  WRITE:/ '60세인 사람의 이름은?', LS_PERSON-NAME.
  
  SORT LT_PERSON BY AGE.
  CLEAR LS_PERSON.
  READ TABLE LT_PERSON INTO LS_PERSON WITH KEY AGE = '60' BINARY SEARCH.
  WRITE:/ LS_PERSON-NAME.
  " 웬만하면 BINARY SEARCH 붙이는 편이 빠르다.
  
  DELETE LT_PERSON WHERE AGE = '60'.
  BREAK-POINT.
  
  CLEAR LT_PERSON_H.
  CLEAR LT_PERSON_H[].
```



| TYPE        | 이미 만들어진 도면이 DB상에 존재한다.( ABAP Dictionary )     |
| ----------- | ------------------------------------------------------------ |
| TYPE REF TO | 이미 만들어진 도면이 DB상에 존재한다.( CLASS/ INTERFACE )    |
| LIKE        | 만들어진 도면은 없으나, 비슷하게 만들수 있는 변수가 존재한다. ( 마치 ~~처럼) |



- INTERNAL TABLE 값 입력 : INSERT, APPEND
- INTERNAL TABLE 값 수정 : MODIFY
  - TRANSPORTING 구문을 이용해 해당 필드만 변경 가능하다.
  - WHER 조건을 통해 조건에 맞는 다수의 RECORD를 수정할 수 있다.
  - INDEX를 이용해 변경하고자 하는 LINE의 값을 변경할 수 있다.

* INTERNAL TABLE을 LOOP하면 SY-TABIX라는 시스템 변수의 값이 1씩 증가한다.



- READ TABLE - INTERNAL TABLE의 한 라인을 읽기 위한 구문

```ABAP
READ TABLE itab WITH KEY f1 = c1.....
READ TALBE itab INDEX index.
```



- BINARY SEARCH 
  - 이진트리를 이용해 값을 찾는 방법.
  - 데이터를 키 값 기준으로 정렬한 후 사용한다.
  - 일반 READ 속도보다 훨씬 빠르다.



- DELETE 구문을 이용한 INTERNAL TABLE의 DATA 삭제

```ABAP
DELETE itab WHERE condition.
" WHERE 조건을 이용한 다수의 라인 삭제

DELETE itab INDEX index.
" INDEX를 이용한 삭제.

DELETE ADJACENT DUPLICATES FROM itab.
DELETE ADJACENT DUPLICATES FROM itab COMPARING field1.
DELETE ADJACENT DUPLICATES FROM itab COMPARING ALL FIELDS.
```



- CLEAR - 메모리 공간 반환
- REFRESH - DATA만 지우고 할당된 메모리는 반환하지 않는다.
  - FREE - 메모리 공간을 반환하기 위해서는 FREE 구문 사용해야 함.
- SORT - BY를 사용해서 원하는 FIELD를 기준으로 정렬할 수 있다.



```ABAP
DATA : BEGIN OF LS_PERSON,
    NAME TYPE CHAR10,
    AGE TYPE NUMC2,
  ADDRESS TYPE CHAR20,
  PHONE TYPE CHAR13,
  END OF LS_PERSON.


 DATA: LT_PERSON LIKE TABLE OF LS_PERSON.

CLEAR: LS_PERSON, LT_PERSON[].

LS_PERSON-NAME = '김홍도'.
LS_PERSON-AGE  = 30.
LS_PERSON-ADDRESS = 'SEOUL'.
LS_PERSON-PHONE = '02-111-1111'.
APPEND LS_PERSON TO LT_PERSON.
CLEAR LS_PERSON.

LS_PERSON-NAME = '신윤복'.
LS_PERSON-AGE  = 20.
LS_PERSON-ADDRESS = 'DAEGU'.
LS_PERSON-PHONE = '053-222-2222'.
APPEND LS_PERSON TO LT_PERSON.
CLEAR LS_PERSON.

LS_PERSON-NAME = '김조년'.
LS_PERSON-AGE  = 40.
LS_PERSON-ADDRESS = 'BUSAN'.
LS_PERSON-PHONE = '051-333-3333'.
APPEND LS_PERSON TO LT_PERSON.
CLEAR LS_PERSON.

LS_PERSON-NAME = '정향'.
LS_PERSON-AGE  = 10.
LS_PERSON-ADDRESS = 'DAEJEON'.
LS_PERSON-PHONE = '042-444-4444'.
APPEND LS_PERSON TO LT_PERSON.
CLEAR LS_PERSON.

LS_PERSON-NAME = '정조'.
LS_PERSON-AGE  = 40.
LS_PERSON-ADDRESS = 'CHEONGJU'.
LS_PERSON-PHONE = '043-555-5555'.
APPEND LS_PERSON TO LT_PERSON.
CLEAR LS_PERSON.

LS_PERSON-NAME = '신영복'.
LS_PERSON-AGE = '50'.
LS_PERSON-ADDRESS = 'DAEGU'.
LS_PERSON-PHONE = '053-666-6666'.
APPEND LS_PERSON TO LT_PERSON.

LS_PERSON-NAME = '장벽수'.
LS_PERSON-AGE = '50'.
LS_PERSON-ADDRESS = 'GWANGJU'.
LS_PERSON-PHONE = '062-777-7777'.
APPEND LS_PERSON TO LT_PERSON.

LS_PERSON-AGE = '18'.
MODIFY LT_PERSON FROM LS_PERSON TRANSPORTING AGE WHERE AGE =< 20.


CLEAR LS_PERSON.
LOOP AT LT_PERSON INTO LS_PERSON.
  IF LS_PERSON-AGE < 20.
    LS_PERSON-PHONE = '전화기가 없습니다.'.
   ELSE.
     LS_PERSON-PHONE = '전화기가 있습니다.'.
     ENDIF.
     MODIFY LT_PERSON FROM LS_PERSON.
    ENDLOOP.

    BREAK-POINT.

*LOOP AT LT_PERSON INTO LS_PERSON.
*  WRITE:/ LS_PERSON-NAME, LS_PERSON-AGE, LS_PERSON-ADDRESS, LS_PERSON-PHONE.
*  ENDLOOP.
```



EX)

```ABAP
PARAMETERS: P_NAME TYPE CHAR10 OBLIGATORY,
P_BDAY TYPE D.

DATA: LV_B_DAY TYPE I,
      LV_AGE TYPE I,
      LV_SEASON TYPE CHAR4.

LV_B_DAY = P_BDAY+4(2).
LV_AGE = 2021 - P_BDAY(4) + 1.

IF 3 <= LV_B_DAY AND LV_B_DAY <= 5.
  LV_SEASON = '봄'.
 ELSEIF 6 <= LV_B_DAY AND LV_B_DAY <= 8.
   LV_SEASON = '여름'.
  ELSEIF 9 <= LV_B_DAY AND LV_B_DAY <= 11.
    LV_SEASON = '가을'.
   ELSE.
     LV_SEASON = '겨울'.
    ENDIF.
    WRITE: P_NAME, '님은 나이가', LV_AGE, '이고', LV_SEASON, '에 태어났습니다.'.
```

```ABAP
DATA: LV_AGE(2) TYPE P,
      LV_SEASON(4).

LV_AGE = SY-DATUM(4) - P_BDAY(4) + 1.

CASE P_BDAY+4(2).
  WHEN '03' OR '04' OR '05'.
    LV_SEASON = '봄'.
   WHEN '06' OR '07' OR'08'.
     LV_SEASON = '여름'.
     WHEN '09' OR '10' OR '11'.
       LV_SEASON = '가을'.
       WHEN OTHERS.
         LV_SEASON = '겨울'.
         ENDCASE.

         WRITE: P_NAME, '님은 나이가', LV_AGE, '이고', LV_SEASON, '에 태어났습니다.'.
```



##### DO

```ABAP
DO [n TIMES].
STATEMENTS....
ENDDO.
```

EX)

```ABAP
  DATA LV_SQUARE TYPE I.

  DO 10 TIMES.
    LV_SQUARE = SY-INDEX ** 2.
    WRITE: / SY-INDEX, LV_SQUARE.
    ENDDO.
```



##### WHILE

```ABAP
WHILE [논리적인 조건].
STATEMENTS....
ENDDO.
```

EX)

```ABAP
DATA LV_TEXT TYPE STRING VALUE 'ONE TWO THREE'.

WHILE SY-SUBRC = 0.
  REPLACE SPACE WITH '-' INTO LV_TEXT.
  ENDWHILE.

  WRITE: LV_TEXT.
```



##### LOOP 문

- LOOP문은 특정한 구문을 반복하여 처리해야 하거나 인터널 테이블에 있는 데이터를 처리할 필요가 있는 경우
- 인터널 테이블의 레코드를 순서대로 읽어와서 처리

```ABAP
LOOP AT itab [RESULT][CONDITION].
STATEMENTS....
ENDLOOP.
```



```ABAP
LOOP AT itab INTO wa
```

- 인터널 테이블의 ITAB의 내용을 한 레코드씩 읽어 wq에 이동한 후, ENDLOOP까지 선언된 내용을 처리한다.

```ABAP
LOOP AT itab ASSIGNING <fs>
```

- 위와 같지만, 레코드의 값을 작업영역에 이동하는 것이 아니라 필드 심벌 <fs>에서 선택한 레코드의 위치를 할당한다.

```ABAP
LOOP AT itab WHERE log_exp
```

- INTERNAL TABLE의 모든 데이터 중에서 log_exp를 만족하는 레코드 대상으로 데이터 처리



- EXIT
- CHECK
- CONTINUE

