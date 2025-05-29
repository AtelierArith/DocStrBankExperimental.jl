```
shih_opp(z::ProductSimplex{T}) where T <: Tuple{AbstractSimplex,AbstractSimplex} -> Linear{T}

積単体 `z` の *反対* エイレンベルグ–マクレーン同相（時には反対シヒマップと呼ばれる）の下での画像を返します。

この関数は線形であり、マクロ `@linear` に記載されているキーワード引数 `coefftype`、`addto`、`coeff`、`sizehint`、`is_filtered` をサポートしています。

他にも [`aw`](@ref)、[`ez`](@ref)、[`shih`](@ref)、[`opposite`](@ref)、[`swap`](@ref)、`LinearCombinations.@linear` を参照してください。

# 例

```

jldoctest julia> x, y = SymbolicSimplex(:x, 2), SymbolicSimplex(:y, 2) (x[0,1,2], y[0,1,2])

julia> a = Linear(ProductSimplex(x, y) => 1)   # ここでは `opposite` から正しい符号を得るために `Linear` を使用します Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 1 term: (x[0,1,2],y[0,1,2])

julia> shih_opp(a) Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 4 terms: -(x[0,0,0,2],y[0,1,2,2])+(x[0,0,1,2],y[0,1,1,2])+(x[0,0,1,2],y[1,2,2,2])-(x[0,1,1,2],y[1,1,2,2])

julia> shih(a) Linear{ProductSimplex{Tuple{SymbolicSimplex{Symbol}, SymbolicSimplex{Symbol}}}, Int64} with 4 terms: -(x[0,1,1,2],y[0,1,2,2])+(x[0,0,1,1],y[0,1,1,2])-(x[0,0,0,1],y[0,1,2,2])+(x[0,0,1,2],y[0,2,2,2])

julia> shih_opp(opposite(swap(a))) == opposite(swap(shih(a))) true ```
