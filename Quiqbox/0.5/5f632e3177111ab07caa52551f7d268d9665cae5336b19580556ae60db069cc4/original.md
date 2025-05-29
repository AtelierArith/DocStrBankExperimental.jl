```
genExponent(e::T, mapFunction::Function=itself; 
            canDiff::Bool=ifelse(Quiqbox.FLevel(mapFunction)==Quiqbox.FLevel{0}, false, true), 
            inSym::Symbol=x_α) where {T<:AbstractFloat} -> 
ParamBox{T, :α}

genExponent(e::Array{T, 0}, mapFunction::Function=itself; 
            canDiff::Bool=ifelse(Quiqbox.FLevel(mapFunction)==Quiqbox.FLevel{0}, false, true), 
            inSym::Symbol=x_α) where {T<:AbstractFloat} -> 
ParamBox{T, :α}

genExponent(eData::Pair{Array{T, 0}, Symbol}, 
            mapFunction::Function=itself; 
            canDiff::Bool=ifelse(Quiqbox.FLevel(mapFunction)==Quiqbox.FLevel{0}, false, true)) where 
           {T<:AbstractFloat} -> 
ParamBox{T, :α}
```

Construct an exponent coefficient given a value or variable (with its symbol).  `mapFunction`, `canDiff`, and `inSym` work the same way as in a general constructor of a  [`ParamBox`](@ref).
