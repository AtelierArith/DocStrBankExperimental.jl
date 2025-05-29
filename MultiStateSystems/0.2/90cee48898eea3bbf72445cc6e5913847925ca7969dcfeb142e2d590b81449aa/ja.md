```
add_transitions!(std::MultiStateSystems.AbstractSTD; kwargs...)
```

状態遷移図 `std` に複数の遷移を追加し、それに対応する `PropDict` を名前付き引数 `kwargs` で埋めます。すべての遷移に対して適用される均一な引数が与えられるか、各遷移に特定の引数を持つ配列が与えられます。

# 例

```julia-repl
julia> stdᵍᵉⁿ = STD()
julia> add_states!(stdᵍᵉⁿ, name  = ["通常運転状態","故障状態"],
                           power = [100.0u"MW",0.0u"MW"],
                           init  = [1.0,0.0],
                           markovian = true)
julia> add_transitions!(stdᵍᵉⁿ, rate = [0.001u"1/hr",0.01u"1/hr"],
                                states = [(1,2),(2,1)])
```

!!! note
    `add_transitions!` 関数で `:states` 引数が提供されていない場合、from-および to-状態は他の引数に基づいて決定されます。


# 例（代替）

```julia-repl
julia> add_transitions!(stdᵍᵉⁿ, rate = [0.000u"1/hr" 0.010u"1/hr"
                                        0.001u"1/hr" 0.000u"1/hr"])
```
