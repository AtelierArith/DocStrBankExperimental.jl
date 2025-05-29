```
cache_edgar_enclosure(cache::HttpCache, enclosure_url)
```

SECからの提出に関連するすべてのXBRLファイルを含むzipフォルダをキャッシュします。

zip圧縮は、自然に繰り返しのテキストを含むxbrl提出に非常に効果的であるため、zipフォルダをダウンロードして抽出する方がはるかに効率的です。これが提出をダウンロードするための最も効率的な方法であることが最も多いです。zipエンクロージャのURLを取得する方法の1つは、SECが提供する構造化開示RSSフィードを通じてです: https://www.sec.gov/structureddata/rss-feeds-submitted-filings
