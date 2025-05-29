```
add_users!(ntw::MultiStateSystems.AbstractNetwork; kwargs...)
```

ネットワーク `ntw` に複数のユーザーを追加し、対応する `PropDict` を名前付き引数 `kwargs` で埋めます。すべてのコンポーネントに対して適用される均一な引数が与えられるか、各コンポーネントに特定の引数が与えられる配列が与えられます。

# 例

```julia-repl
julia> ntwᵖʷʳ = ntw()
julia> add_sources!(ntwᵖʷʳ, node = [1,5,8],
                            ind  = [:EENS])
```
