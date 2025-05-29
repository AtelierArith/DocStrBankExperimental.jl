```julia
sigqueue(pid, sig, val=0)
```

プロセス識別子 `pid` に信号 `sig` を送信します。引数 `val` は信号に結合するオプションの値です。この値は C 型 `union sigval`（C の `int` と C の `void*` の共用体）を表し、Julia では両方の種類の値を表すのに十分な大きさの整数として指定されます。
