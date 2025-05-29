```
s = remote_signal(f, args...; init = nothing, procid = first(workers()))
```

`init`で初期化された信号を作成します。信号のアクション`f(args...)`は、引数が更新されるたびに、`procid`のプロセスでリモートで実行されます。リモート信号はプッシュベースのパラダイムでのみ機能します。
