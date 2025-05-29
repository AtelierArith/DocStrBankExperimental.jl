```
cache_edgar_enclosure(cache::HttpCache, enclosure_url)
```

Cache the zip folder from SEC containing all XBRL related files for a given submissions.

Due to the fact that the zip compression is very effective on xbrl submissions that naturally contain repeating text, it is way more efficient to download the zip folder and extract it. This will most often be the most efficient method for downloading the submission. One way to get the zip enclosure url is through the Structured Disclosure RSS Feeds provided by the SEC: https://www.sec.gov/structureddata/rss-feeds-submitted-filings
