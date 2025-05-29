```
midcor(X::AbstractMatrix; dims=1, c=9)
```

バイウェイトミッドコレlationを使用して相関行列を計算します。デフォルトでは、行列の各列が別々の変数であるため、`dims=1`の`(M, N)`行列は`(N, N)`の相関行列を作成します。ただし、`dims=2`の場合、各行が変数になり、`(M, M)`の相関行列が生成されます。対角線は常に1になります。

# 例

```jldoctest
julia> X = 10 .* randn(rng, 1000, 3) .+ 50;


julia> C = midcor(X)
3×3 Matrix{Float64}:
  1.0        -0.0108271  -0.0286201
 -0.0108271   1.0        -0.0050253
 -0.0286201  -0.0050253   1.0

julia> size(midcor(X; dims=2))
(1000, 1000)
```

# 参考文献

1. [Wikipedia](https://en.wikipedia.org/wiki/Biweight_midcorrelation)
2. [NIST: Biweight midcorrelation](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwmidcr.htm)

# 関連項目

[`midvar`](@ref), [`midcov`](@ref), [`scale`](@ref)
