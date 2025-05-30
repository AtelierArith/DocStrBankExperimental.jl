```julia
KrylovJL(args...; KrylovAlg = Krylov.gmres!,
    Pl = nothing, Pr = nothing,
    gmres_restart = 0, window = 0,
    kwargs...)
```

Krylov.jlのクリロフ部分空間反復ソルバーの一般的なラッパーです。
