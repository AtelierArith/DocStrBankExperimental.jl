```
ArrayFactors(af::Vector{<:AbstractArray}, di::DimIndices)
ArrayFactors(af::Vector{<:AbstractArray}, di::Vector)
ArrayFactors(af::Vector{<:AbstractArray})
```

配列因子は、配列の要素がその積であるように定義されています: `M[i, j, ..., l] = af[1][i] * af[2][j] * ... * af[3][l]`。

配列因子は、ベクトルまたは多次元配列自体であることができます。

ArrayFactorsの主な用途は、多次元配列のメモリ効率の良い表現として、`Array()`メソッドを使用して構築できることです。

参照: [`ipf`](@ref), [`ArrayMargins`](@ref), [`DimIndices`](@ref)

# フィールド

  * `af::Vector{<:AbstractArray}`: (多次元)配列因子のベクトル
  * `di::DimIndices`: 配列因子が属する次元インデックス。

# 例

```julia-repl
julia> AF = ArrayFactors([[1,2,3], [4,5]])
サイズ (3, 2) の配列の因子:
  [1]: [1, 2, 3]
  [2]: [4, 5]

julia> eltype(AF)
Int64

julia> Array(AF)
3×2 Matrix{Int64}:
  4   5
  8  10
 12  15

julia> AF = ArrayFactors([[1,2,3], [4 5; 6 7]], DimIndices([2, [1, 3]]))
3D配列の因子:
  [2]: [1, 2, 3]
  [1, 3]: [4 5; 6 7]

julia> Array(AF)
2×3×2 Array{Int64, 3}:
[:, :, 1] =
 4   8  12
 6  12  18

[:, :, 2] =
 5  10  15
 7  14  21
```
