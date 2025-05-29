```
set_uni_integral_defaults(; kwargs...)::Nothing
```

1次元積分のデフォルトキーワード引数設定を行います。この関数のキーワード引数は、デフォルトキーワード引数辞書に記録されます。これにより、単一の無限パラメータを持つ[`integral`](@ref MeasureToolbox.integral(::JuMP.AbstractJuMPScalar,::InfiniteOpt.GeneralVariableRef,::Real, ::Real))を呼び出す際のデフォルトキーワード引数の値が決まります。

**例**

```julia-repl
julia> uni_integral_defaults()
Dict{Symbol,Any} with 1 entry:
  :eval_method => Automatic()


julia> set_uni_integral_defaults(num_supports = 5, eval_method = Quadrature(),
                                 new_kwarg = true)

julia> uni_integral_defaults()
Dict{Symbol,Any} with 3 entries:
  :new_kwarg             => true
  :num_supports          => 5
  :eval_method           => Quadrature()
```
