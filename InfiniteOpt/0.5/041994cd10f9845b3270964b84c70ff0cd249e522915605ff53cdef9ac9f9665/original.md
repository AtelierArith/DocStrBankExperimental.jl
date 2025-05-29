```
all_parameters(model::InfiniteModel,
               type::Type{InfOptParameter} = InfOptParameter
               )::Vector{GeneralVariableRef}
```

Return a list of all the `InfiniteOpt` parameters assigned to `model`. By default, all of the infinite and finite parameters is returned. The search is reduced to a particular type is obtained by specifying the concrete parameter type of [`InfOptParameter`](@ref) via `type`. Type options include:

  * `InfOptParameter`: all parameters
  * `ScalarParameter`: all scalar parameters
  * `InfiniteParameter`: all infinite parameters
  * `FiniteParameter`: all finite parameters
  * `IndependentParameter`: all independent infinite parameters
  * `DependentParameters`: all dependent infinite parameters

**Examples**

```julia-repl
julia> all_parameters(model)
4-element Array{GeneralVariableRef,1}:
 t
 x[1]
 x[2]
 alpha

julia> all_parameters(model, FiniteParameter)
1-element Array{GeneralVariableRef,1}:
 alpha
```
