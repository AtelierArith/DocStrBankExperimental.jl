```
add_components!(ntw::MultiStateSystems.AbstractNetwork; kwargs...)
```

ネットワーク `ntw` に複数のコンポーネントを追加し、それらの対応する `PropDict` を名前付き引数 `kwargs` で埋めます。すべてのコンポーネントに対して適用される均一な引数が与えられるか、各コンポーネントに特定の引数を持つ配列が与えられます。

# 例

```julia-repl
julia> ntwᵖʷʳ = ntw()
julia> add_components!(ntwᵖʷʳ, edge = [(1,2),(1,2),(2,3)],
                               name = ["cable 1","cable 2","cable 3"],
                               std  = [STD(power = [0u"MW",1500u"MW"],
                                           prob  = [0.2,0.8]),
                                       STD(power = [0u"MW",2000u"MW"],
                                           prob  = [0.4,0.6]),
                                       STD(power = [0u"MW",1800u"MW",4000u"MW"],
                                           prob = [0.1,0.2,0.7])])
```
