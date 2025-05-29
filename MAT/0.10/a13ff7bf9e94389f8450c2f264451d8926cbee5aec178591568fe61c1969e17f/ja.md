```
matopen(filename [, mode]; compress = false) -> handle
matopen(f::Function, filename [, mode]; compress = false) -> f(handle)
```

モードはデフォルトで読み取り用の `"r"` です。書き込み用の `"w"` または、作成や切り捨てなしの読み取りまたは書き込み用の `"r+"` にすることもできます。

読み取り時の圧縮は自動的に検出/処理されます。`compress` キーワード引数は書き込み操作のみに影響します。

`read`、`write`、`close`、`keys`、および `haskey` と一緒に使用します。
