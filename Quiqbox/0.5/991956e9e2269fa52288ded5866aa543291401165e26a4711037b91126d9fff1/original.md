```
markParams!(b::Union{AbstractVector{T}, T, Tuple{T, Vararg{T}}}, 
            filterMapping::Bool=false) where {T<:ParameterizedContainer} -> 
Vector{<:ParamBox}
```

Mark the parameters ([`ParamBox`](@ref)) in `b`. The parameters that hold the same  independent variable (in other words, considered identical in the differentiation  procedure) will be marked with same index. `filterMapping` determines whether filtering out  (i.e. not return) the extra `ParamBox`es that hold the same independent variables but  represent different output variables. The independent variable held by a `ParamBox` can be  inspected using [`indVarOf`](@ref).
