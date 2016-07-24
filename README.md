## Naver News Search API

#### 요청

- start : 검색의 시작 위치 지정. 최소 1 ~ 최대 1000
- sort : 유사도 순, 날짜 순 검색 가능(날짜 순은 광고글이 많음)
- display : 검색 시 최소 1개 ~ 최대 100개씩 보여줄 수 있음



#### 응답

- total : 총 결과 문서의 개수 (실제적으로 확인 가능한 뉴스는 4000개)

  ![스크린샷 2016-07-24 오후 2.17.11](/Users/HSH/Desktop/스크린샷 2016-07-24 오후 2.17.11.png)

- lastBuildDate : 검색 결과를 생성한 시간을 의미 (최근 사용자들이 검색한 데이터를 종합할 때 사용해도 좋을듯)

- originallink : 기사 제공 언론사 link

- link : 네이버 기사 link (존재하지 않은 경우에는 기사 제공한 언론사 link로 감)

  ![스크린샷 2016-07-24 오후 1.54.17](/Users/HSH/Desktop/스크린샷 2016-07-24 오후 1.54.17.png)

- title : 유일호 부총리 "`사드` 로 인한 중국 비관세장벽 우려... ...."

- description : 주한미군의 `사드`(THAAD-고고도미사일방어체계) 배치로 인한 중국의 경제보복 확률은 매우 낮을 것이라고... => 검색 결과 문서의 내용을 요약한 정보.

- pubDate : publish 된 시간(기사가 네이버에 제공된 시간)  ex) 1시간 전



## 요청 예시

```
GET v1/search/news.xml?query=%EC%A3%BC%EC%8B%9D&display=10&start=1&sort=sim HTTP/1.1
Host: openapi.naver.com
User-Agent: curl/7.43.0
Accept: */*
Content-Type: application/xml
X-Naver-Client-Id: {애플리케이션 등록 시 발급받은 client id 값}
X-Naver-Client-Secret: {애플리케이션 등록 시 발급받은 secret값}
```



## 응답 예시

```xml
<rss version="2.0">
<channel>
        <title>Naver 오픈 API - news ::'sample'</title>
        <link>http://search.naver.com</link>
        <description>Naver Search Result</description>
        <lastBuildDate>Tue, 25 Jun 2013 16:07:52 +0900</lastBuildDate>
        <total>3033</total>
        <start>1</start>
        <display>10</display>
        <item>
                <title>Cheonan food expo draws 53 foreign firms</title>
                <originallink>
                        http://www.koreatimes.co.kr/www/news/nation/2013/06/116_138059.html
                </originallink>
                <link>
                        http://openapi.naver.com/l AAABWIyQ6DIBgGn+bnaCrU7cDBre/B8hESU0sRNbx96WQOk/meiFnSOtMoaJr/0U80LCzlALnjPtiGLE2tn49WC251AUDjuBKttaYuv3PMRzjpUwokRuKv4gEVja92dSFW5vP+AW4sCndqAAAA
                </link>
                <description>
                                “The foreign firms are expected to display their diverse food products and provide visitors with the opportunity to <b>sample</b> them, making the expo a stage to grasp the recent trend of well...
                </description>
                <pubDate>Mon, 24 Jun 2013 19:14:00 +0900</pubDate>
        </item>
        <item>
                <title>FSS to limit bank CEOs' paychecks</title>
                <originallink>
                        http://www.koreatimes.co.kr/www/news/biz/2013/06/488_138036.html
                </originallink>
                <link>
                        http://openapi.naver.com/l?AAABWIyQ6DIBgGn+bnaCrU7cDBre/B8hESU0sRNbx96WQOk/meiFnSOtMoaJr/0U80LCzlALnjPtiGLE2tn49WC251AUDjuBKttaYuv3PMRzjpUwokRuKv4gEVja92dSFW5vP+AW4sCndqAAAA
                </link>
                <description>
                        Our <b>sample</b> survey showed that some financial firms are operating questionable salary systems for executives and directors,” an FSS official said. “We’ve decided to launch a full...
                </description>
                <pubDate>Mon, 24 Jun 2013 17:29:00 +0900</pubDate>
        </item>
....
</channel>
</rss>
```

