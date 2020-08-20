# :runner: MySQL
- [Programmers SQL 고득점 Kit](https://programmers.co.kr/learn/challenges) 문제 풀이  

### :bulb: SELECT
- 모든 레코드 조회하기  
```mysql
SELECT * FROM ANIMAL_INS
/* SELECT * FROM 테이블명 */
```
- 역순 정렬하기  
```mysql
SELECT NAME,DATETIME FROM ANIMAL_INS ORDER BY ANIMAL_ID DESC
/*SELECT (출력할 열) FROM (테이블명) ORDER BY (정렬기준이 되는 열) DESC // ASC = 오름차순, DESC = 내림차순으로 정렬*/
```

- 아픈 동물 찾기 
```MYSQL
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION='SICK'
/* = ANIMAL_ISN 테이블에 INTAKE_CONDITION 이 SICK인 ANIMAL_ID,NAME을 출력*/
/* SELECT (출력할 열) FROM (테이블명) WHERE (찾을 조건)*/
```

- 어린 동물 찾기
```MYSQL
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION != 'aged' ORDER BY ANIMAL_ID ASC
/* = ANIMAL_INS 테이블에서 INTAKE_CONDITION 이 aged가 아닌 모든 값중 오름차순으로 정렬해서 ANIMAL_ID,NAME을 출력*/
/* SELECT (출력할 열) FROM (테이블명) WHERE (찾을 값의 조건) ORDER BY (정렬 기준이 되는 열) ASC */
```

- 동물의 아이디와 이름
```mysql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS ORDER BY ANIMAL_ID ASC
/* ANIMAL_INS 테이블에서 ANIMAL_ID를 오름차순으로 정렬 후 ANIMAL_ID,NAME을 출력*/
```

- 여러 기준으로 정렬하기
```mysql
SELECT ANIMAL_ID, NAME, DATETIME 
FROM ANIMAL_INS 
ORDER BY NAME ASC,DATETIME DESC
/* ANIMAL_INS 테이블의 데이터를 NAME순으로 정렬 후, DATETIME을 역순으로 정렬하여 ANIMAL_ID,NAME, DATETIME을 출력*/
```
- 상위 n개 레코드
```mysql
SELECT NAME FROM ANIMAL_INS
ORDER BY DATETIME
LIMIT 1
/* ANIMAL_INS 테이블에서 DATETIME 기준으로 정렬 후 NAME 을 1개만 출력*/
```

### :bulb: SUM,MAX,MIN
 - 최댓값 구하기
```mysql
/* 가장 최근의 DATETIME값을 찾기 */

SELECT DATETIME FROM ANIMAL_INS ORDER BY DATETIME DESC LIMIT 1
/* ANIMAL_INS 테이블에서 DATETIME을 역순으로 정렬 후 상위 1개만 출력*/

SELECT MAX (DATETIME) FROM ANIMAL_INS
/* ANIMAL_INS 테이블에서 DATETIME의 MAX값 출력*/
```

- 최솟값 구하기
```mysql
SELECT DATETIME FROM ANIMAL_INS ORDER BY DATETIME ASC LIMIT 1
/* ANIMAL_INS 테이블에서 DATETIME을 오름차순으로 정렬 후 상위 1개만 출력*/

SELECT MIN (DATETIME) FROM ANIMAL_INS
/* ANIMAL_INS 테이블에서 DATETIME의 MIN값 출력*/
```

- 동물 수 구하기
```mysql
SELECT COUNT(DATETIME) AS count FROM ANIMAL_INS
/* ANIMAL_INS 테이블에 DATETIME열의 데이터 수를 세어서 count 라는 열을 만들어 저장*/
```

- 중복 제거하기
```MYSQL
SELECT COUNT(DISTINCT NAME) FROM ANIMAL_INS
/* ANIMAL_INS 테이블에 NAME의 갯수를 중복을 제거하고(DISTINCT) 세어 출력*/
```
### :bulb: Group by

- 고양이와 개는 몇마리 있을까?
```mysql
SELECT ANIMAL_TYPE, COUNT(ANIMAL_ID)
FROM ANIMAL_INS
GROUP BY ANIMAL_TYPE
ORDER BY ANIMAL_TYPE ASC
/* ANIMAL_INS 테이블에서 ANIMAL_TYPE과 ANIMAL_ID 수를 세어 출력
ANIMAL_TYPE 을 그룹으로 묶어 오름차순정렬 */
```
- 동명의 동물 찾기
```MYSQL
SELECT NAME, COUNT(DISTINCT ANIMAL_ID) AS count
FROM ANIMAL_INS
GROUP BY NAME
HAVING COUNT(NAME) > 1
ORDER BY NAME
/* ANIMAL_INS 테이블에서 NAME, ANIMAL_ID를 중복없이 세어 count열로 출력
NAME 으로 그룹핑(조건 NAME COUNT가 1보다 큰것만 이름순으로 나열) 
```
