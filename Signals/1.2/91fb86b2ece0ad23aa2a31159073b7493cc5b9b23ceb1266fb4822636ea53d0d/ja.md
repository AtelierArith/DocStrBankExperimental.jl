```
s = async_signal(f, args...; init = nothing)
```

`init`で初期化された信号を作成します。`f(args...)`のアクションは、引数が更新されるたびに別のタスクで非同期に実行されます。非同期信号はプッシュベースのパラダイムでのみ機能します。
