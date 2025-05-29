```
ExpiringCaches.Cache{K, V}(timeout::Dates.Period; purge_on_timeout::Bool=false)
```

スレッドセーフな期限切れキャッシュを作成します。`timeout` より古い値は「無効」となり、削除されます。

`ExpiringCaches.Cache` は `AbstractDict` であり、すべての点で通常の `Dict` をエミュレートしようとします。値の取得や計算のコストが高く、一定の時間キャッシュできる場合に最も便利です。キャッシュを使用しないようにするため（つまり、キャッシュを無効にするため）、`Cache` は値を手動で削除するための `delete!` および `empty!` メソッドをサポートしています。

デフォルトでは、期限切れのキーは要求されるまでキャッシュに残ります（`haskey` または `get` を介して）。`purge_on_timeout=true` キーワード引数が渡されると、エントリごとに非同期タスクが生成されます。タイムアウトタスクが `timeout` の長さの時間待機すると、キーはキャッシュから削除されます。
