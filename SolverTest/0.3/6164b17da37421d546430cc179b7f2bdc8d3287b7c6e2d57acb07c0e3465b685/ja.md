```
kkt_checker(nlp, sol; kwargs...)
```

与えられた NLPModels `nlp` とベクトル `sol` に対して、最適化問題の KKT 残差をタプル (primal, dual) として返します。特に、次の線形制約を持つ二次最適化問題を解くために `ripqp` を使用します。

```
min_{d} ∇f(sol)ᵀd +  ½∥d∥²
        lvar ≤ sol + d ≤ uvar
        lcon ≤ c(sol) + ∇c(sol)d ≤ ucon
```

この問題の解は、目的関数の ½ ‖d‖² 項のおかげで、`sol` における `nlp` のラグランジアンの勾配です。

キーワード引数は `RipQP` に渡されます。
