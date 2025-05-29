(

```julia
BifurcationProblem(_F, u0, parms; ...)
BifurcationProblem(
    _F,
    u0,
    parms,
    lens;
    jvp,
    vjp,
    J,
    J!,
    Jᵗ,
    d2F,
    d2Fc,
    d3F,
    d3Fc,
    issymmetric,
    record_from_solution,
    plot_solution,
    delta,
    save_solution,
    inplace,
    update!,
    kwargs_jet...
)

```

)

バイフルケーション問題のコンストラクタ。

## オプション引数
