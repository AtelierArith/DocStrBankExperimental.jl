```
getParams(pbc::ParamBox, symbol::Union{Symbol, Missing}=missing) -> 
Union{ParamBox, Nothing}

getParams(pbc::ParameterizedContainer, symbol::Union{Symbol, Missing}=missing) -> 
AbstractVector{<:ParamBox}

getParams(pbc::Union{AbstractArray{<:T}, Tuple{T, Vararg{T}}}, 
          symbol::Union{Symbol, Missing}=missing) where {T<:QuiqboxContainer} -> 
AbstractVector{<:ParamBox}
```

Return the parameter(s) stored in the input container. If `symbol` is set to `missing`,  then return all the parameter(s). If it's set to a `Symbol` tied to a parameter, for  example `:α₁`, the function will match any `pb::`[`ParamBox`](@ref) such that  [`indVarOf`](@ref)`(pb)[begin] == :α₁`. If it's set to a `Symbol` without any subscript,  for example `:α`, the function will match it with all the `pb`s such that  `string(indVarOf(pb)[begin])` contains `'α'`. If the first argument is a collection, its  entries must be `ParamBox` containers.
