```
markParams!(b::Union{AbstractVector{T}, T, Tuple{T, Vararg{T}}}, 
            filterMapping::Bool=false) where {T<:ParameterizedContainer} -> 
Vector{<:ParamBox}
```

`b`のパラメータ（[`ParamBox`](@ref)）にマークを付けます。同じ独立変数を保持するパラメータ（言い換えれば、微分手続きにおいて同一と見なされる）は、同じインデックスでマークされます。`filterMapping`は、同じ独立変数を保持するが異なる出力変数を表す余分な`ParamBox`をフィルタリング（すなわち、返さない）するかどうかを決定します。`ParamBox`が保持する独立変数は、[`indVarOf`](@ref)を使用して調査できます。
