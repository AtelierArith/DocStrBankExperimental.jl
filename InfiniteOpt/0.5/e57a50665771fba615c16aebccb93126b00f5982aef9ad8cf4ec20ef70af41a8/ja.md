```
set_optimizer_model_ready(model::InfiniteModel, status::Bool)
```

最適化モデルのステータスを最新かどうかに設定します。この関数は主に内部用ですが、拡張に役立ちます。

**例**

```julia-repl
julia> set_optimizer_model_ready(model, true)

julia> optimizer_model_ready(model)
true
```
