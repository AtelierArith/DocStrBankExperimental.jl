```
num_parameters(model::InfiniteModel,
               [type::Type{InfOptParameter} = InfOptParameter])::Int
```

Return the number of `InfiniteOpt` parameters assigned to `model`. By default, the total number of infinite and finite parameters is returned. The amount of a particular type is obtained by specifying the concrete parameter type of [`InfOptParameter`](@ref) via `type`. Type options include:

  * `InfOptParameter`: all parameters
  * `ScalarParameter`: all scalar parameters
  * `InfiniteParameter`: all infinite parameters
  * `FiniteParameter`: all finite parameters
  * `IndependentParameter`: all independent infinite parameters
  * `DependentParameters`: all dependent infinite parameters

**Example**

```julia-repl
julia> num_parameters(model)
3

julia> num_parameters(model, IndependentParameter)
2
```
