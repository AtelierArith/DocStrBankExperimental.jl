```julia
gettimeofday() -> tv
```

は、`IPC.TimeVal`のインスタンスとして現在の時刻を返します。結果は、`float(tv)`を呼び出すことで小数秒に変換できます。

参照: [`IPC.TimeVal`](@ref), [`nanosleep`](@ref), [`clock_gettime`](@ref).
