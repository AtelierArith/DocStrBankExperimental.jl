```
match_all(query::AbstractQuery, corpus::Corpus)
```

`corpus`内のすべての文書から`query`のすべての一致を探します。見つかったすべての一致に対応する`QueryMatch`オブジェクトの`Vector`を返します。
