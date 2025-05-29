```
select_vocabulary(corpus; 
    min_document_frequency=1, transform=identity, pattern=r"\w\w+\b", stopwords=Set{String}())
```

コーパスからキーワード引数で定義されたルールに基づいて単語を選択します。ストップワードは語彙リストから除外されます。`stopwords=default_stop_words()`を使用して、Sci-kit Learnから単語のリストを取得します。
