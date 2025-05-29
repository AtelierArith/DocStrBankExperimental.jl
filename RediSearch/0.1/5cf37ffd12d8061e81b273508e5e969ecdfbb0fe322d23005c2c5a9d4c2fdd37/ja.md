```
search(q::AbstractQuery; client=get_search_client()) -> Result
```

クエリオブジェクトを使用して、RediSearchを検索します。

# 引数

  * `q::AbstractQuery`: クエリオブジェクト。

# キーワード

  * `client`: 検索されるクライアント。
