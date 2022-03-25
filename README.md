# WeView

세미프로젝트 영화리뷰사이트 WeView입니다.

테이블 쿼리문

CREATE TABLE MOVIE(
    SEQ_MOVIE	NUMBER(3,0) PRIMARY KEY,
    TITLE	VARCHAR2(100 BYTE) NOT NULL,
    GENRE	VARCHAR2(20 BYTE) NOT NULL,
    DIRECTOR	VARCHAR2(50 BYTE) NOT NULL,
    COUNTRY	VARCHAR2(20 BYTE) NOT NULL,
    ACTOR	VARCHAR2(500 BYTE) NOT NULL,
    CREATED	DATE,
    AGE	NUMBER(2,0) NOT NULL,
    RUNNINGTIME	NUMBER(3,0) NOT NULL,
    STORY	VARCHAR2(2000 BYTE) NOT NULL,
    RATE	NUMBER(2,1) NOT NULL,
    TRAILER	VARCHAR2(50 BYTE),
    POSTER	VARCHAR2(50 BYTE)
);

CREATE TABLE MEMBER(
    SEQ_MEMBER	NUMBER(10,0) PRIMARY KEY,
    ID	VARCHAR2(50 BYTE) UNIQUE NOT NULL,
    PWD	VARCHAR2(60 BYTE) NOT NULL,
    NAME	VARCHAR2(50 BYTE) NOT NULL,
    EMAIL	VARCHAR2(150 BYTE) UNIQUE NOT NULL,
    NICKNAME	VARCHAR2(50 BYTE) UNIQUE NOT NULL,
    CREATEDATE	DATE,
    PROFILE	NUMBER(38,0) NOT NULL
);

CREATE TABLE FAVORITEMOVIE(
    SEQ_FM NUMBER(10) PRIMARY KEY,
    LISTNUMBER NUMBER(10) NOT NULL,
    SEQ_USER NUMBER(10) NOT NULL,
    POSTER VARCHAR2(50) NOT NULL,
    CONSTRAINT FK_SEQ_USER FOREIGN KEY(SEQ_USER) REFERENCES MEMBER(SEQ_MEMBER)
);

CREATE TABLE FAVORITEGENRE(
    SEQ_FG NUMBER(10) PRIMARY KEY,
    SEQ_USER NUMBER(10) NOT NULL,
    ACTION INTEGER NOT NULL,
    FANTASY INTEGER NOT NULL,
    SF INTEGER NOT NULL,
    COMEDY INTEGER NOT NULL,
    ROMANCE INTEGER NOT NULL,
    THRILLER INTEGER NOT NULL,
    CONSTRAINT FK_SEQ_USER2 FOREIGN KEY(SEQ_USER) REFERENCES MEMBER(SEQ_USER)
);

CREATE TABLE COMMENTS(
    SEQ_COMMENT NUMBER(10) PRIMARY KEY,
    ID VARCHAR2(50) NOT NULL,
    CONTENT VARCHAR2(2000) NOT NULL,
    CREATED DATE,
    RATE INTEGER NOT NULL,
    SEQ_MOVIE NUMBER(10) NOT NULL,
    CONSTRAINT FK_SEQ_COMMENT FOREIGN KEY(SEQ_MOVIE) REFERENCES MOVIE(SEQ_MOVIE)
    );

CREATE TABLE REQUEST(
    SEQ_REQUEST NUMBER(10) PRIMARY KEY,
    ID VARCHAR2(50) NOT NULL,
    TITLE VARCHAR2(100) NOT NULL,
    CONTENT VARCHAR2(2000) NOT NULL,
    CREATED DATE
);
