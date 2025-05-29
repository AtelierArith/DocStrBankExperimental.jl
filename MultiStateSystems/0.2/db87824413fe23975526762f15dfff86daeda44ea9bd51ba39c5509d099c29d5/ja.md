```
add_states!(std::MultiStateSystems.AbstractSTD; kwargs...)
```

状態遷移図 `std` に複数の状態を追加し、それに対応する `PropDict` を名前付き引数 `kwargs` で埋めます。すべての状態に対して適用される均一な引数が与えられるか、各状態に対する特定の引数を持つ配列が与えられます。

# 例

```julia-repl
julia> stdᵍᵉⁿ = STD()
julia> add_states!(stdᵍᵉⁿ, name  = ["normal operation state","failed state"],
                           power = [100.0u"MW",0.0u"MW"],
                           init  = [1.0,0.0],
                           markovian = true)
```
