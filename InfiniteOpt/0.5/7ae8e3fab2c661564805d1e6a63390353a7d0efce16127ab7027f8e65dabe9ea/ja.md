```
JuMP.get_optimizer_attribute(model::InfiniteModel,
                             attr::MOI.AbstractOptimizerAttribute)
```

`get_optimizer_attribute`を拡張して、`model`内のソルバー固有の属性`attr`の値を返します。

**例** `julia-repl julia> get_optimizer_attribute(model, MOI.Silent()) true`
