```julia
sigaction(signum) -> sigact
```

は、プロセスが信号 `signum` を受信したときに取る現在のアクション（[`SigAction`](@ref) のインスタンス）を返します。

```julia
sigaction(signum, sigact)
```

は、プロセスが信号 `signum` を受信したときに取るアクションとして `sigact`（[`SigAction`](@ref) のインスタンス）をインストールします。

`signum` は `SIGKILL` または `SIGSTOP` であってはならないことに注意してください。

さらに [`SigAction`](@ref) と [`sigaction!`](@ref) を参照してください。
