```
JuMP.delete(model::InfiniteModel, cref::InfOptConstraintRef)::Nothing
```

`JuMP.delete`を拡張して、`InfiniteOpt`制約とすべての関連情報を削除します。`cref`が無効な場合はエラーを返します。

**例**

```julia-repl
julia> print(model)
Min measure(g(t)*t) + z
Subject to
 z ≥ 0.0
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]

julia> delete(model, cref)

julia> print(model)
Min measure(g(t)*t) + z
Subject to
 z ≥ 0.0
```
