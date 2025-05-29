```
all_derivatives(model::InfiniteModel)::Vector{GeneralVariableRef}
```

Returns a list of all the individual derivatives stored in `model`. 

**Example**

```julia-repl
julia> all_derivatives(model)
3-element Array{GeneralVariableRef,1}:
 ∂/∂t[T(x, t)]
 ∂/∂x[T(x, t)]
 ∂/∂x[∂/∂x[T(x, t)]]
```
