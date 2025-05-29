```
JuMP.delete(model::InfiniteModel, mref::MeasureRef)::Nothing
```

`JuMP.delete`を拡張して、測度を削除します。測度が無効な場合、つまりモデルに属していないか、すでに削除されている場合はエラーになります。

**例**

```julia-repl
julia> print(model)
Min ∫{t ∈ [0, 6]}[g(t)] + z
Subject to
 z ≥ 0.0
 ∫{t ∈ [0, 6]}[g(t)] = 0
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]
 g(0.5) = 0

julia> delete(model, meas)

julia> print(model)
Min z
Subject to
 z ≥ 0.0
 0 = 0
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]
 g(0.5) = 0
```
