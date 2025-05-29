```julia
solveCliqWithStateMachine!(
    dfg,
    tree,
    frontal;
    iters,
    downsolve,
    recordhistory,
    verbose,
    nextfnc,
    prevcsmc
)

```

単一クリークのためのスタンドアロン状態遷移マシンソリューション。

関連:

initInferTreeUp!
