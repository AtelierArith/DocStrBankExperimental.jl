```
JuMP.get_optimizer_attribute(model::InfiniteModel, name::String)
```

`get_optimizer_attribute`を拡張して、`name`という名前のソルバー固有の属性に関連付けられた値を返します。

**例** `julia-repl julia> get_optimizer_attribute(model, "tol") 0.0001``
