```
JuMP.set_optimizer_attribute(model::InfiniteModel,
                             attr::MOI.AbstractOptimizerAttribute,
                             value)
```

`set_optimizer_attribute`を拡張して、`model`内のソルバー固有の属性`attr`を`value`に設定します。

**例**

```julia-repl
julia> set_optimizer_attribute(model, MOI.Silent(), true)
true
```
