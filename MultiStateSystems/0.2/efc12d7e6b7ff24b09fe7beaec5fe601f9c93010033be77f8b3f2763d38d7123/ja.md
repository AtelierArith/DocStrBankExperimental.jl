```
add_source!(ntw::MultiStateSystems.AbstractNetwork; kwargs...)
```

ネットワーク `ntw` に単一のソースを追加し、対応する `PropDict` を名前付き引数 `kwargs` で埋めます。

# 例

```julia-repl
julia> ntwᵖʷʳ = ntw()
julia> stdᵍᵉⁿ = solvedSTD(prob = [0.1,0.2,0.7],
                          flow = [0.0u"MW",0.5u"MW",2.0u"MW"])
julia> add_source!(ntwᵖʷʳ, node = 1,
                           name = "generator 1",
                           std  = stdᵍᵉⁿ)
```
