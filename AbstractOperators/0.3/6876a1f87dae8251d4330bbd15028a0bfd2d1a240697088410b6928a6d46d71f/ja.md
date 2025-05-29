`RDFT([domainType=Float64::Type,] dim_in::Tuple [,dims=1])`

`RDFT(dim_in...)`

`RDFT(x::AbstractArray [,dims=1])`

実数配列 `x` に対して掛け算を行うと、次元 `dims` にわたるDFTを返す `LinearOperator` を作成します。これはエルミート対称性を利用しています。

```julia
julia> RDFT(Float64,(10,10))
ℱ  ℝ^(10, 10) -> ℂ^(6, 10)

julia> RDFT((10,10,10),2)
ℱ  ℝ^(10, 10, 10) -> ℂ^(10, 6, 10)

```
