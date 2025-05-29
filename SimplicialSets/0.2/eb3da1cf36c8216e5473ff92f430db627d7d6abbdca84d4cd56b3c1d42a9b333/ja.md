```
ez(x::AbstractSimplex...) -> ProductSimplex

ez(AbstractTensor{T}) where T <: Tuple{Vararg{AbstractSimplex}} -> ProductSimplex{T}
```

与えられた単体の画像をエイレンベルグ–ジルバーまたはシャッフル写像の下で返します。最初のバージョンは単体に対して多重線形であり、2番目のバージョンはテンソル引数に対して線形です。ゼロを含む任意の数の単体が許可されます。

この関数は、マクロ `@linear` に記載されている `coefftype`、`addto`、`coeff`、`sizehint`、および `is_filtered` というキーワード引数をサポートしています。

関連情報として [`aw`](@ref)、[`shih`](@ref)、`LinearCombinations.@linear` を参照してください。

# 例

```jldoctest
julia> x, y = SymbolicSimplex(:x, 1), SymbolicSimplex(:y, 2)
(x[0,1], y[0,1,2])

julia> a = ez(x, y)
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 3 terms:
(x[0,1,1,1],y[0,0,1,2])-(x[0,0,1,1],y[0,1,1,2])+(x[0,0,0,1],y[0,1,2,2])

julia> ez(Tensor(x, y); addto = a, coeff = -1)
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 0 terms:
0

julia> z = SymbolicSimplex(:z, 0)
z[0]

julia> ez(x, y, z)
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 3 terms:
(x[0,1,1,1],y[0,0,1,2],z[0,0,0,0])-(x[0,0,1,1],y[0,1,1,2],z[0,0,0,0])+(x[0,0,0,1],y[0,1,2,2],z[0,0,0,0])

julia> ez(x, y, z) == ez(ez(x, y), z)
false

julia> ez(x)
Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}}}, Int64} with 1 term:
(x[0,1])

julia> ez(Tensor())
Linear{ProductSimplex{Tuple{}}, Int64} with 1 term:
()
```
