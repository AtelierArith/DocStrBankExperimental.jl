```
JuMP.set_optimizer_attribute(model::InfiniteModel, name::String, value)
```

`set_optimizer_attribute`を拡張して、`name`で識別されるソルバー固有の属性を`value`に指定します。

**例**

```julia-repl
julia> set_optimizer_attribute(model, "SolverSpecificAttributeName", true)
true
```
