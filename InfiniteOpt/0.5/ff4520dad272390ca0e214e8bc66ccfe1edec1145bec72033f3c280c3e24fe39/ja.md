```
all_derivatives(model::InfiniteModel)::Vector{GeneralVariableRef}
```

`model`に保存されているすべての個別の導関数のリストを返します。

**例**

```julia-repl
julia> all_derivatives(model)
3-element Array{GeneralVariableRef,1}:
 ∂/∂t[T(x, t)]
 ∂/∂x[T(x, t)]
 ∂/∂x[∂/∂x[T(x, t)]]
```
