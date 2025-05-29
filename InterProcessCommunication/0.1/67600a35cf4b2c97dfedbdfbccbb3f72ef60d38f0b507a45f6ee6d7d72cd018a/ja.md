```julia
sigaction!(signum, sigact, oldact) -> oldact
```

は、信号 `signum` を受信したときにプロセスが取るアクションとして `sigact` をインストールし、以前のアクションである `oldact` を上書きして返します。引数 `sigact` と `oldact` は [`SigAction`](@ref) のインスタンスです。

詳細については、[`SigAction`](@ref) と [`sigaction`](@ref) を参照してください。
