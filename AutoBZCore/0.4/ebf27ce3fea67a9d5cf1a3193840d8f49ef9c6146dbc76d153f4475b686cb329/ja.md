```
init(::IntegralProblem, ::IntegralAlgorithm; kws...)::IntegralSolver
```

[`IntegralProblem`](@ref)、[`IntegralAlgorithm`](@ref)、およびソルバーへのキーワード引数（すなわち `abstol`、`reltol`、または `maxiters`）のキャッシュを構築し、同じタイプの異なるパラメータに対して問題を解くために再利用できるようにします。
