```julia
plotVariableGivenFactor(dfg, fct, towards; levels, dims)

```

変数yに対する因子xの新しい提案（畳み込み）を、他のすべての変数を考慮してプロットします。すなわち、y|X

ノート

  * `towards`に新しい結果を最初の色としてプロットします。
  * 因子内の他の変数を2番目からm色でプロットします。
