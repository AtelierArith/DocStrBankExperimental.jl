```
add_transition!(std::MultiStateSystems.AbstractSTD; kwargs...)
```

状態遷移図 `std` に単一の遷移を追加し、対応する `PropDict` を名前付き引数 `kwargs` で埋めます。必須の名前付き引数は `:states` で、from-および to-状態のタプル (fr,to) を説明します。

# 例

```julia-repl
julia> stdᵍᵉⁿ = STD()
julia> add_states!(stdᵍᵉⁿ, name  = ["normal operation state","failed state"],
                           power = [100.0u"MW",0.0u"MW"],
                           init  = [1.0,0.0],
                           markovian = true)
julia> add_transition!(stdᵍᵉⁿ, rate = 0.001u"1/hr",
                               states = (1,2))
```
