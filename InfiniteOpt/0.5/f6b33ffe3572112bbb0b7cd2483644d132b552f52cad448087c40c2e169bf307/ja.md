```
JuMP.set_optimizer_attributes(model::InfiniteModel, pairs::Pair...)
```

`set_optimizer_attributes`を拡張して、`attribute => value`ペアのリストを指定して複数のソルバー属性を設定します。各ペアに対して`set_optimizer_attribute(model, attribute, value)`を呼び出します。

**例**

```julia-repl
julia> model = Model(Ipopt.Optimizer);

julia> set_optimizer_attributes(model, "tol" => 1e-4, "max_iter" => 100)
```

は次のように等価です：

```julia-repl
julia> set_optimizer_attribute(model, "tol", 1e-4);

julia> set_optimizer_attribute(model, "max_iter", 100);
```
