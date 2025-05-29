```
arraydist(dists::AbstractArray{<:Distribution})
```

サブ分布の配列から積分布を作成します。`dists`の各要素は同じサイズである必要があります。各要素のサイズが`(d1, d2, ...)`であり、`size(dists)`が`(n1, n2, ...)`である場合、結果の分布はサイズ`(d1, d2, ..., n1, n2, ...)`になります。

デフォルトの動作は、[`Distributions.product_distribution`](https://juliastats.org/Distributions.jl/stable/multivariate/#Distributions.product_distribution)を直接使用することですが、これは時々特化されることがあります。

# 例

```jldoctest; setup=:(using Distributions, Random)
julia> d1 = arraydist([Normal(0, 1), Normal(10, 1)])
Product{Continuous, Normal{Float64}, Vector{Normal{Float64}}}(v=Normal{Float64}[Normal{Float64}(μ=0.0, σ=1.0), Normal{Float64}(μ=10.0, σ=1.0)])

julia> size(d1)
(2,)

julia> Random.seed!(42); rand(d1)
2-element Vector{Float64}:
 0.7883556016042917
 9.1201414040456

julia> d2 = arraydist([Normal(0, 1) Normal(5, 1); Normal(10, 1) Normal(15, 1)])
DistributionsAD.MatrixOfUnivariate{Continuous, Normal{Float64}, Matrix{Normal{Float64}}}(
dists: Normal{Float64}[Normal{Float64}(μ=0.0, σ=1.0) Normal{Float64}(μ=5.0, σ=1.0); Normal{Float64}(μ=10.0, σ=1.0) Normal{Float64}(μ=15.0, σ=1.0)]
)

julia> size(d2)
(2, 2)

julia> Random.seed!(42); rand(d2)
2×2 Matrix{Float64}:
 0.788356   4.12621
 9.12014   14.2667
```
