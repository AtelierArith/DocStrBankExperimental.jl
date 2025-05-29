```
add_components!(ntw::MultiStateSystems.AbstractNetwork; kwargs...)
```

ネットワーク `ntw` に単一のコンポーネントを追加し、対応する `PropDict` を名前付き引数 `kwargs` で埋めます。

# 例

```julia-repl
julia> ntwᵖʷʳ = ntw()
julia> add_components!(ntwᵖʷʳ, edge = (1,2),
                               name = "cable 1",
                               std  = STD(power = [0u"MW",1500u"MW"],
                                          prob  = [0.2,0.8]))
```
