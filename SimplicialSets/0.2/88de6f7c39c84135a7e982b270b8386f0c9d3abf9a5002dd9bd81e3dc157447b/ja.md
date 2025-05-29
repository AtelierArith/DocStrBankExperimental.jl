```
shih(z::ProductSimplex{T}) where T <: Tuple{AbstractSimplex,AbstractSimplex} -> Linear{T}
shih_eml(z::ProductSimplex{T}) where T <: Tuple{AbstractSimplex,AbstractSimplex} -> Linear{T}

Eilenberg–MacLane ホモトピーの下での積単体 `z` の像を返します（これは時々 Shih マップと呼ばれます）。

この関数は線形であり、マクロ `@linear` に記載されているキーワード引数 `coefftype`、`addto`、`coeff`、`sizehint`、`is_filtered` をサポートしています。

関連情報として [`aw`](@ref)、[`ez`](@ref)、[`shih_opp`](@ref)、`LinearCombinations.@linear` を参照してください。

# 例

```

jldoctest julia> x, y = SymbolicSimplex(:x, 2), SymbolicSimplex(:y, 2); z = ProductSimplex(x, y) (x[0,1,2],y[0,1,2])

julia> shih(z) Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 4 terms: -(x[0,1,1,2],y[0,1,2,2])+(x[0,0,1,1],y[0,1,1,2])-(x[0,0,0,1],y[0,1,2,2])+(x[0,0,1,2],y[0,2,2,2])

julia> shih(ez(x, y)) Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 0 terms: 0

julia> shih(ez(x, y)) Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 0 terms: 0

julia> aw(shih(z)) Linear{Tensor{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 0 terms: 0

julia> shih(shih(z)) Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 0 terms: 0 ```
