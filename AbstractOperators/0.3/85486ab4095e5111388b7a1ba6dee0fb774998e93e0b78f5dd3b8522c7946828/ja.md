`DCAT(A::AbstractOperator...)`

ブロック対角に `AbstractOperator` を連結します。

```julia
julia> D = DCAT(HCAT(Eye(2),Eye(2)),DFT(3))
[[I,I],0;0,ℱ]  ℝ^2  ℝ^2  ℝ^4 -> ℝ^2  ℂ^3

julia> DCAT(Eye(10),Eye(10),FiniteDiff((4,4)))
DCAT  ℝ^10  ℝ^10  ℝ^(4, 4) -> ℝ^10  ℝ^10  ℝ^(3, 4)
```

`DCAT` 演算子を評価するには、正しいドメインサイズとタイプの `AbstractArray` の `Tuple` でそれらを掛けます。出力は、`DCAT` のコドメインタイプとサイズを持つ `Tuple` でも構成されます。

```julia
julia> D*ArrayPartition(ones(2),ones(2),ones(3))
([2.0, 2.0], Complex{Float64}[3.0+0.0im, 0.0+0.0im, 0.0+0.0im])

```
