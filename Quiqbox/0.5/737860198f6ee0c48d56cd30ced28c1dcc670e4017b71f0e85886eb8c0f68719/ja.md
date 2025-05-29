```
genSpatialPoint(comp::T, compIndex::Int, 
                mapFunction::Function=itself; 
                canDiff::Bool=ifelse(FLevel(mapFunction)==IL, false, true), 
                inSym::Symbol=(:x_X, :x_Y, :x_Z)[compIndex]) where {T<:AbstractFloat} -> 
ParamBox{T}

genSpatialPoint(comp::Array{T, 0}, compIndex::Int, 
                mapFunction::Function=itself; 
                canDiff::Bool=ifelse(FLevel(mapFunction)==IL, false, true), 
                inSym::Symbol=(:x_X, :x_Y, :x_Z)[compIndex]) where {T<:AbstractFloat} -> 
ParamBox{T}

genSpatialPoint(compData::Pair{Array{T, 0}, Symbol}, compIndex::Int, 
                mapFunction::Function=itself; 
                canDiff::Bool=ifelse(FLevel(mapFunction)==IL, false, true)) -> 
ParamBox{T}
```

[`ParamBox`](@ref) を構築して、値または変数（そのシンボルを持つ）を与えられたときに [`SpatialPoint`](@ref) の `compIndex` 番目のコンポーネントを生成します。 `mapFunction`、`canDiff`、および `inSym` は、`ParamBox` の一般的なコンストラクタと同じように機能します。

```
genSpatialPoint(point::ParamBox{T}, compIndex::Int) where {T<:AbstractFloat} -> 
ParamBox{T}
```

`ParamBox` を `SpatialPoint` の `compIndex` 番目のコンポーネントに変換します。

≡≡≡ 例 ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> genSpatialPoint(1.2, 1)
ParamBox{Float64, :X, …}{0}[∂][X]⟦=⟧[1.2]

julia> pointY1 = fill(2.0);

julia> Y1 = genSpatialPoint(pointY1, 2)
ParamBox{Float64, :Y, …}{0}[∂][Y]⟦=⟧[2.0]

julia> pointY1[] = 1.5;

julia> Y1
ParamBox{Float64, :Y, …}{0}[∂][Y]⟦=⟧[1.5]
```
