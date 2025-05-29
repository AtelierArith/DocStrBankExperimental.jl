```julia
initAll!(dfg; ...)
initAll!(dfg, solveKey; _parametricInit, solvable, N)

```

`solvable=1`（デフォルト）で全ての変数に対して`graphinit`を実行します。

参照: [`ensureSolvable!`](@ref), (実験的 'treeinit')
