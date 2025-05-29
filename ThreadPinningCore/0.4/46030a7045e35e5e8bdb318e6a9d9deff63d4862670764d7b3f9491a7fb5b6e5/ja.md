```
threadids(; threadpool = :default)
```

指定されたスレッドプール内のJuliaスレッドのIDを取得します。

`:default`および`:interactive`に加えて、`threadpool`キーワード引数は`:all`（`:default` + `:interactive`スレッド用）および`:gc`（GCスレッド用）に設定できます。後者のオプションは現時点では実験的であり、いつでも変更または廃止される可能性があることに注意してください。
