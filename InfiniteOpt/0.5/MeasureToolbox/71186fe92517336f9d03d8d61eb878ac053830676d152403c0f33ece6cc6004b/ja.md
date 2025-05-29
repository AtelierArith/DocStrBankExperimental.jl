```
@integral(expr::JuMP.AbstractJuMPScalar,
          prefs::Union{GeneralVariableRef, AbstractArray{GeneralVariableRef}},
          [lower_bounds::Union{Real, AbstractArray{<:Real}} = default_bounds,
          upper_bounds::Union{Real, AbstractArray{<:Real}} = default_bounds;
          kwargs...])::GeneralVariableRef
```

[`integral`](@ref integral(::JuMP.AbstractJuMPScalar, ::InfiniteOpt.GeneralVariableRef, ::Real, ::Real)) と [`integral`](@ref integral(::JuMP.AbstractJuMPScalar, ::AbstractArray{InfiniteOpt.GeneralVariableRef}, ::Union{Real, AbstractArray{<:Real}}, ::Union{Real, AbstractArray{<:Real}}) の効率的なラッパーです。詳細については、上記のドキュメント文字列を参照してください。
