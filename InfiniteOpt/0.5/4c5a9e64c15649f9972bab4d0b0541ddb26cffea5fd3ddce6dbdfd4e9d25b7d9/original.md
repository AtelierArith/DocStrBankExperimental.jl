```
JuMP.all_variables(model::InfiniteModel, [type])::Vector{GeneralVariableRef}
```

Extend `JuMP.all_variables`] to return a list of all the variable references  associated with `model`. By default, all of the infinite, semi-infinite, point,  and finite variables is returned. Those of a particular type is obtained by  specifying the concrete variable type via `type`. Type options include:

  * `InfiniteVariable`: all infinite variables
  * `SemiInfiniteVariable`: all semi-infinite variables
  * `PointVariable`: all point variables
  * `FiniteVariable`: all finite variables

**Examples**

```julia-repl
julia> all_variables(model)
4-element Array{GeneralVariableRef,1}:
 y(t)
 w(t, x)
 y(0)
 z

julia> all_variables(model, PointVariable)
1-element Array{GeneralVariableRef,1}:
 y(0)
```
