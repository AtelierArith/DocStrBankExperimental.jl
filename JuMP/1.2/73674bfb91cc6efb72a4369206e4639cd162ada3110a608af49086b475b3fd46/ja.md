```
set_optimizer_attributes(model::Model, pairs::Pair...)
```

与えられた `attribute => value` ペアのリストに対して、各ペアに対して `set_optimizer_attribute(model, attribute, value)` を呼び出します。

## 例

```julia
model = Model(Ipopt.Optimizer)
set_optimizer_attributes(model, "tol" => 1e-4, "max_iter" => 100)
```

は次のように等価です：

```julia
model = Model(Ipopt.Optimizer)
set_optimizer_attribute(model, "tol", 1e-4)
set_optimizer_attribute(model, "max_iter", 100)
```

参照： [`set_optimizer_attribute`](@ref), [`get_optimizer_attribute`](@ref).
