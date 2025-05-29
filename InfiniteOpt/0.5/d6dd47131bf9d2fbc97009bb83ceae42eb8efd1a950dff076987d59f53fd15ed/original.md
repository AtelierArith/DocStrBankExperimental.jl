```
JuMP.num_variables(model::InfiniteModel, [type])::Int
```

Extend `JuMP.num_variables` to return the number of `InfiniteOpt` variables  assigned to `model`. By default, the total number of infinite, semi-infinite,  point, and finite variables is returned. The amount of a particular type is  obtained by specifying the concrete variable type via `type`. Type options  include:

  * `InfiniteVariable`: all infinite variables
  * `SemiInfiniteVariable`: all semi-infinite variables
  * `PointVariable`: all point variables
  * `FiniteVariable`: all finite variables

**Example**

```julia-repl
julia> num_variables(model)
3

julia> num_variables(model, InfiniteVariable)
2
```
