```
VarianceFTest(x::AbstractVector{<:Real}, y::AbstractVector{<:Real})
```

2つの実数ベクトル `x` と `y` が等しい分散を持つという帰無仮説のF検定を実行します。

実装: [`pvalue`](@ref)

# 参考文献

  * George E. P. Box, "Non-Normality and Tests on Variances", Biometrika 40 (3/4): 318–335, 1953.

# 外部リンク

  * [F-test of equality of variances on Wikipedia](https://en.wikipedia.org/wiki/F-test_of_equality_of_variances)
