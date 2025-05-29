```julia
sigwait!(mask, info, timeout=Inf) -> signum
```

は [`sigwait`](@ref) のように動作しますが、追加の引数 `info` は受け入れたシグナルに関する情報を格納するための [`SigInfo`](@ref) のインスタンスです。他の引数は [`sigwait`](@ref) メソッドと同様です。
