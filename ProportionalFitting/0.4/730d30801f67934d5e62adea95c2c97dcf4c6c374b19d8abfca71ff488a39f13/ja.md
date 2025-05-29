```
ArrayMargins(am::Vector{<:AbstractArray}, di::DimIndices)
ArrayMargins(am::Vector{<:AbstractArray}, di::Vector)
ArrayMargins(am::Vector{<:AbstractArray})
ArrayMargins(X::AbstractArray, di::DimIndices)
ArrayMargins(X::AbstractArray)
```

ArrayMarginsは配列の周辺和であり、これらの和が属する次元のインデックスと組み合わされています。周辺和自体も多次元配列である可能性があります。

ArrayMarginsには、生の周辺またはその周辺が計算される実際の配列に基づいたさまざまなコンストラクタがあります。

参照: [`DimIndices`](@ref), [`ArrayFactors`](@ref), [`ipf`](@ref)

# フィールド

  * `am::Vector{AbstractArray}`: 周辺和のベクトル。
  * `di::DimIndices`: `am`の要素が属する次元インデックス。

# 例

```julia-repl
julia> X = reshape(1:12, 2, 3, 2)
2×3×2 reshape(::UnitRange{Int64}, 2, 3, 2) with eltype Int64:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12

julia> ArrayMargins(X)
Margins from 3D array:
  [1]: [36, 42]
  [2]: [18, 26, 34]
  [3]: [21, 57]

julia> ArrayMargins(X, [1, [2, 3]])
Margins from 3D array:
  [1]: [36, 42]
  [2, 3]: [3 15; 7 19; 11 23]

julia> ArrayMargins(X, [2, [3, 1]])
Margins of 3D array:
  [2]: [18, 26, 34]
  [3, 1]: [9 12; 27 30]
```
