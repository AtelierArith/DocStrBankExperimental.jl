```julia
psolver_cg_matrix(
    setup;
    kwargs...
) -> IncompressibleNavierStokes.var"#psolve!#104"{Base.Pairs{Symbol, Union{}, Tuple{}, @NamedTuple{}}}

```

共役勾配反復ポアソンソルバー。`kwargs`はIterativeSolvers.jlの`cg!`関数に渡されます。
