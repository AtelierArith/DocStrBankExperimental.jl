```
JuMP.delete(model::InfiniteModel, vref::DecisionVariableRef)::Nothing
```

`JuMP.delete`を拡張して`InfiniteOpt`変数とその依存関係を削除します。変数が無効な場合、つまりすでに削除されているか、別のモデルに属している場合はエラーが発生します。

**例**

```julia-repl
julia> print(model)
Min measure(g(t)*t) + z
Subject to
 z ≥ 0.0
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]
 g(0.5) = 0

julia> delete(model, g)

julia> print(model)
Min measure(t) + z
Subject to
 z ≥ 0.0
 z ≥ 42.0
```
