```
@integral(expr::JuMP.AbstractJuMPScalar,
          prefs::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef}},
          [lower_bounds::Union{Real, AbstractArray{<:Real}} = default_bounds,
          upper_bounds::Union{Real, AbstractArray{<:Real}} = default_bounds;
          kwargs...])::GeneralVariableRef
```

An efficient wrapper for [`integral`](@ref integral(::JuMP.AbstractJuMPScalar, ::InfiniteOpt.GeneralVariableRef, ::Real, ::Real)) and [`integral`](@ref integral(::JuMP.AbstractJuMPScalar, ::AbstractArray{InfiniteOpt.GeneralVariableRef}, ::Union{Real, AbstractArray{<:Real}}, ::Union{Real, AbstractArray{<:Real}})). Please see the above doc strings for more information.
