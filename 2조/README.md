# 2조 GooglePlaystore EDA

#### 팀장: 박지호
#### 팀원: 안세정, 유채원, 이서현, 한예림  

발표에 활용된 코드는 code 폴더에 정리되어 있습니다.
  
<img src = "https://user-images.githubusercontent.com/97828157/182591463-889894ff-f9db-498f-a09f-a026cf8e4201.jpg" width = '200' height = '200'/>
    

## EDA 내용 정리

1. 데이터  

       - 어플 정보 데이터: googleplaystore.csv 
       - 어플 리뷰 데이터: googleplaystore_user_reviews.csv  
 
2. 데이터 전처리  

       - 결측치 drop  
       - 문자열 -> 숫자형 변환 


3. 기초 분석  
    
       - 목표 설정: 어플의 성공 전략 분석  
       - feature 상관관계 분석: Installs와 Reviews의 상관관계 ↑, 의외로 Installs와 Rating의 상관관계 ↓  
       - 카테고리에 따른 installs 분석  
         ※ Insight: 카테고리별 Installs가 상이한 것은 카테고리마다 특성이 다르다는 것. 카테고리를 나누어 분석해보자!
       - Outlier 제거 후의 installs 분석: 성공률이 높은, 독점시장이 아닌 카테고리 선정
       - 리뷰 데이터 전체에서의 워드클라우드 분석
    
4. 카테고리별 분석  
    
        - 선정된 카테고리 분석: Entertainment, Photography, Shopping, Game, Education   
    
       < Entertainment >  
         어플 데이터 분석
          - Installs가 높은 어플 중 무료의 비중이 상대적으로 높다  
          - 카테고리내의 최저 Installs 값이 상대적으로 높다 -> 망할 확률이 낮다
       
         리뷰 데이터 분석(워드 클라우드)
          - watch, show, ad ↑
    
       < Photography >
         리뷰 데이터 분석(워드 클라우드)
          - Installs 상위권 어플의 'video'가 많고 중위권에는 'ad'가 많다
    
       < Shopping >
         리뷰 데이터 분석(워드 클라우드)
          - Installs 상위권 어플의 경우 'groupon', 'deal', 'price' 가 많다
            -> 소비자가 할인을 중요시 하는 걸로 추측
    
       < Game >  
         어플 데이터 분석
         - 평균 Installs vs Outlier를 제거한 평균 Installs 비교: 감소폭이 작은 편
           -> 유행이 빠르다는 게임 카테고리의 특성상 독점이 덜할 것임 
         - 연령 제한에 따른 평균 Installs 분석: 10세이상, 전연령, 성인 순으로 높음
           -> 어린아이를 위한 전연령의 게임보다는 약간의 자극이 있는 게임이 높아보임
         - 어플의 용량 분석: Installs가 높을수록 어플의 용량이 큼
           -> 고사양의 게임, 많은 컨텐츠를 담기위해선 큰 용량 필요
       
       < Education >
          어플 데이터 분석
          - 다른 어플들과 다르게 Rating과 Installs간의 상관관계 ↑
            -> 평점 관리도 중요한 카테고리라고 추측 가능
         
          리뷰 데이터 분석(워드클라우드)
          - 'learn', 'langauge', 'another language' ↑ 
            -> 어플의 사용목적이 언어인 경우가 많고 다른 언어의 버전을 원하는 리뷰가 많음

5. 결론 전략  

       1. 추천 카테고리: 독점시장이 아니면서 성공률(Installs)이 높은 카테고리
      
         Entertainment, Photography, Shopping, Game, Education
      
       2. 추천 카테고리별 전략 
          1) Entertainment:
          
             - 영상 시청이 주
             - 팝업 광고 자제
             - 실시간 방송에 참여시키는 등 다른 방법으로 수익 창출 추천
       
          2) Photography:  
          
             - 전통적인 사진 편집 이외의 비디오 편집 기능이 대세
       
          3) Shopping:     
          
             -할인 쿠폰 활용 전략 추천
       
          4) Game:       
          
             - 연령제한 10+의 게임 제작 추천
             - 주기적인 업데이트 필요
             - 유행에 맞는 게임 제작 추천
       
          5) Education:     
            
             - 언어 학습 장르가 인기
             - 다양한 국적의 이용자를 타겟으로(매끄러운 번역 중요)
     
        3. 기타 전략:
          
             - 독점 시장을 노려보고 싶다면 차별화 시도!(ex. Communication의 Between 어플)
     
        4. 한계점 및 더 알아보고 싶은 점 : 
          
             - Installs 수가 범주형 수치였기에 정확한 추정에 대한 한계
             - 국가별 데이터를 활용하면 국가별로 적합한 전략을 세울 수 있었을 것
                               

## 주차별 작업내용   
<details> 
<summary>  1주차  </summary>  

> 안세정  
> - csv 파일 불러오기  
> - 결측치 탐색, dropna로 결측치 제거, fillna로 결측치 보간  
> - ‘Reviews’ 열 전처리: M을 *1,000,000으로 변환한 뒤 문자형을 숫자형으로 변환
> - ‘Installs’ 열 전처리: +와 , 제거한 뒤 문자형을 숫자형으로 변환  
  
> 유채원
> - 결측치 제거, 및 버전 카테고리 슬라이싱으로 제외
> - 함수 설정으로 string을 float으로 전환
> - rank로 순위 매겨보기
  
> 이서현
> - 데이터 파악
> - 결측치 확인 데이터 병합 일부 결측치 제거

> 한예림
> - 데이터 불러오고 간단하게 요약 및 데이터 파악
> - 추후 작업 계획: 전처리( + 표시 제거, missing columns 처리 방법, size 단위 통일, varies with device, datatype 변경 등 )  
추가적으로 새로운 변수 만들어 통계 파악 쉽도록. (rating - 숫자로 퍼져있는 값들을 범위 지정해 정리)
</details>

<details>
<summary>  2주차    </summary>
  
> 안세정  
> > 작업내용:   
> > - 구글 플레이스토어 전체 무료 앱을 인기순으로 추출  
> > - 구글 플레이스토어 금일 기종별 (휴대전화, 태블릿, TV, Chromebook) Top 10 게임추출  
> >
> > 인사이트:  
> > - 기종 별로 인기가 많은 게임 앱 순위가 아주 달랐다 = 게임 개발자들이 상품을 개발할 때 타겟하려는 기종을 확실히 정해두는 것이 우월전략 같아보임 + 게임 개발시 기종 별 호환에 신경 써야 함

> 유채원:  
> - review 데이터 전처리 - 결측치 제거, groupby로 앱별 sentiment 값 평균 내기
> - 크롤링 : 구글 앱스토어 최고매출 10위 이름, 별점, 다운로드 수 크롤링 하기
> - 부족한 점: 크롤링 시에 selenium으로 앱 하나하나 클릭해서 다운로드 수를 가져왔는데 시간이 너무 오래 걸려 10개밖에 못함/ 크롤링 할 때마다 앱 이름이 출력되는 경우, 안 되는 경우가 번갈아 나타남

> 이서현:  
> > - 데이터 전처리 : 실수화, 단위 통일 groupby로 카테고리별 Installs 비교
> > - 리뷰데이터 미존재 결과 삭제, 평점 선형보간법으로 보간
> > - 분석 : Ratings와 상관관계 있는 요소 알아보았으나 유료앱에서 약간 높은 별점분포를 보인다는 것 말고 별도의 insight 없었음 
> > - 크롤링 : 구글 플레이스토어 어플 리뷰 크롤링/한계 : 데이터 부족, eda 내용과 연관 많이 없음

> 한예림:  
> > 전처리 완료
> > - size -> 전부 mb로 통일
> > - installs -> , + 제거하고 숫자로 변환
> > - 이상치 (index 10472) 삭제
> > - 결측치 -> 일부는 sklearn으로 median 처리. 일부는 삭제.
>
> > 분석
> > - review 수 많은 순으로 나열 -> 인기 많은 어플.(review 수로 어플의 성공을 판단할 수 있지 않을까)
> > - 일단 수치적으로 높은 상관 관계를 보였던 건 review와 installs 였지만 더 자세한 분석을 해봐야 알 수 있을 것 같음.

</details>


<details>
<summary> 3주차  </summary>

> 안세정, 유채원:  
> > - 워드클라우드를 활용한 전체 데이터 및 카테고리별 리뷰 시각화
>
> 한예림, 이서현:
> > - feature의 상관관계 시각화  
> > - 카테고리별 installs, review등의 feature 시각화


</details> 
 
