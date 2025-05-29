```
add_state!(std::MultiStateSystems.AbstractSTD; kwargs...)
```

状態遷移図 `std` に単一の状態を追加し、対応する `PropDict` を名前付き引数 `kwargs` で埋めます。

# 例

```julia-repl
julia> stdᵍᵉⁿ = STD()
julia> add_state!(stdᵍᵉⁿ, name  = "normal operation state",
                          power = 100u"MW",
                          init  = 1.0)
```
