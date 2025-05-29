```julia
IterativeSolversJL(args...;
    generate_iterator = IterativeSolvers.gmres_iterable!,
    Pl = nothing, Pr = nothing,
    gmres_restart = 0, kwargs...)
```

IterativeSolvers.jl ソルバーの一般的なラッパーです。

!!! note
    このソルバーを使用するには、パッケージ IterativeSolvers.jl を追加する必要があります。すなわち、`using IterativeSolvers`

