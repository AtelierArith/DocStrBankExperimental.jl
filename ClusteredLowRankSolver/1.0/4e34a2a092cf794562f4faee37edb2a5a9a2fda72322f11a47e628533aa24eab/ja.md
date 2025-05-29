```
exact_solution(problem::Problem, primalsol::PrimalSolution, dualsol::DualSolution; transformed=false, FF = QQ, g=1, settings::RoundingSettings=RoundingSettings(), monomial_bases=nothing)
```

問題に対する正確な解を計算して返します。与えられたプライマル解、デュアル解、および近似生成子 `g` を持つフィールド `FF` に基づいています。`transformed=false` の場合は `(success, exactdualsol)` を返し、`transformed=true` の場合は `(success, pd_transformed_exactsolution, transformations)` を返します。
