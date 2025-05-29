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

Construct a [`ParamBox`](@ref) as the `compIndex` th component of a [`SpatialPoint`](@ref)  given a value or variable (with its symbol). `mapFunction`, `canDiff`, and `inSym` work  the same way as in a general constructor of a `ParamBox`.

```
genSpatialPoint(point::ParamBox{T}, compIndex::Int) where {T<:AbstractFloat} -> 
ParamBox{T}
```

Convert a `ParamBox` to the `compIndex` th component of a `SpatialPoint`.

≡≡≡ Example(s) ≡≡≡

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
