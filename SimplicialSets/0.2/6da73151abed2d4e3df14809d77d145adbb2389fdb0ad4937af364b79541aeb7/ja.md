```
aw(x::ProductSimplex{T}) where T <: Tuple{Vararg{AbstractSimplex}} -> Linear{Tensor{T}}
```

与えられた積単体のアレクサンダー・ホイットニー写像の下での画像を返します。積単体は、ゼロを含む任意の数の成分を持つことができます。結果のテンソル積の成分の数は、積単体の成分の数と同じです。

この関数は線形であり、マクロ `@linear` に記載されているように、キーワード引数 `coefftype`、`addto`、`coeff`、および `is_filtered` をサポートしています。

関連項目としては [`coprod`](@ref)、[`ez`](@ref)、[`shih`](@ref)、`LinearCombinations.@linear` があります。

# 例

```jldoctest
julia> x, y = SymbolicSimplex(:x, 2), SymbolicSimplex(:y, 2)
(x[0,1,2], y[0,1,2])

julia> aw(ProductSimplex(x, y))
Linear{Tensor{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 3 terms:
x[0]⊗y[0,1,2]+x[0,1,2]⊗y[2]+x[0,1]⊗y[1,2]

julia> z = SymbolicSimplex(:z, 2); aw(ProductSimplex(x, y, z))
Linear{Tensor{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 6 terms:
x[0,1]⊗y[1]⊗z[1,2]+x[0,1,2]⊗y[2]⊗z[2]+x[0,1]⊗y[1,2]⊗z[2]+x[0]⊗y[0]⊗z[0,1,2]+x[0]⊗y[0,1]⊗z[1,2]+x[0]⊗y[0,1,2]⊗z[2]

julia> aw(ProductSimplex(x))
Linear{Tensor{Tuple{SymbolicSimplex{Symbol}}}, Int64} with 1 term:
x[0,1,2]

julia> aw(ProductSimplex(; dim = 0))
Linear{Tensor{Tuple{}}, Int64} with 1 term:
()
```
