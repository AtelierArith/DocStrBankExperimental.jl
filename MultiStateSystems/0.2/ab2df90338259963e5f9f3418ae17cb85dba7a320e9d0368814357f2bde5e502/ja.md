```
add_sources!(ntw::MultiStateSystems.AbstractNetwork; kwargs...)
```

ネットワーク `ntw` に複数のソースを追加し、それに対応する `PropDict` を名前付き引数 `kwargs` で埋めます。すべてのコンポーネントに対して適用される均一な引数が与えられるか、各コンポーネントに特定の引数が与えられる配列が与えられます。

# 例

```julia-repl
julia> ntwᵖʷʳ = ntw()
julia> stdᵍᵉⁿ = solvedSTD(prob = [0.1,0.2,0.7],
                          flow = [0.0u"MW",0.5u"MW",2.0u"MW"])
julia> add_sources!(ntwᵖʷʳ, node = 1:5,
                            std  = stdᵍᵉⁿ,
                            dep  = true)
```
