```
solve_truss(values::Vector{Float64}, p::TrussOptParams; linsolve_alg = UMFPACKFactorization())
```

分析ステップの後にすべての関連する中間変数を解決して保存します。この関数は、すべての後続の構造解析の基礎です。
