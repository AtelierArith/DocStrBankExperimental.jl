```
match_all(query::AbstractQuery, document::Document)
```

ドキュメント内の `query` に対するすべての一致を探します。見つかったすべての一致に対応する `Vector` `QueryMatch` オブジェクトを返します。
