```julia
psolver_cg(
    setup;
    abstol,
    reltol,
    maxiter,
    preconditioner
) -> IncompressibleNavierStokes.var"#psolve!#110"{_A, _B, _C, IncompressibleNavierStokes.var"#laplace_diag#108"{ndrange, workgroupsize}} where {_A, _B, _C, ndrange, workgroupsize}

```

共役勾配反復ポアソンソルバー。
