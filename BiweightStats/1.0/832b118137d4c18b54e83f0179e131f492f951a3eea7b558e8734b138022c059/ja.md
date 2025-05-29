```
midcov(X::AbstractMatrix; dims=1, c=9)
```

バイウェイトミッド共分散を使用して分散共分散行列を計算します。デフォルトでは、各列が別々の変数であるため、`dims=1`の`(M, N)`行列は`(N, N)`共分散行列を作成します。ただし、`dims=2`の場合、各行が変数となり、`(M, M)`共分散行列が生成されます。

!!! warning
    共分散計算では`NaN`および`Inf`を削除できないため、これらが存在する場合、返される値は`NaN`になります。これを防ぐために、非有限データに対して値を補完することを検討してください。


# 例

```jldoctest
julia> X = 10 .* randn(rng, 1000, 3) .+ 50;


julia> C = midcov(X)
3×3 Matrix{Float64}:
 100.918    -1.05846    -2.88515
  -1.05846  94.702      -0.490742
  -2.88515  -0.490742  100.699

julia> size(midcov(X; dims=2))
(1000, 1000)
```

# 参考文献

1. [NIST: biweight midcovariance](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwmidc.htm)

# 関連項目

[`scale`](@ref), [`midvar`](@ref), [`midcor`](@ref)
