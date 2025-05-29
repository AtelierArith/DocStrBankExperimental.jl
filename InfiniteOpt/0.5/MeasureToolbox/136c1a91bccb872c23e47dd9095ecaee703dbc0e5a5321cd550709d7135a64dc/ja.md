```
set_multi_integral_defaults(; kwargs...)::Nothing
```

多次元積分のデフォルトキーワード引数設定を行います。この関数のキーワード引数はデフォルトキーワード引数辞書に記録されます。これにより、無限のパラメータの配列を持つ[`integral`](@ref MeasureToolbox.integral(::JuMP.AbstractJuMPScalar,::AbstractArray{GeneralVariableRef},::Union{Real, AbstractArray{<:Real}}, ::Union{Real, AbstractArray{<:Real}}))を呼び出す際のデフォルトキーワード引数の値が決まります。

**例**

```julia-repl
julia> multi_integral_defaults()
Dict{Symbol,Any} with 1 entry:
  :eval_method => Automatic()

julia> set_multi_integral_defaults(num_supports = 5, new_kwarg = true)

julia> multi_integral_defaults()
Dict{Symbol,Any} with 3 entries:
  :new_kwarg             => true
  :num_supports          => 5
  :eval_method           => Automatic()
```
