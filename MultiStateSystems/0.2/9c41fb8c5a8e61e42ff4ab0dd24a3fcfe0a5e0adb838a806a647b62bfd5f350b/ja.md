```
add_user!(ntw::MultiStateSystems.AbstractNetwork; kwargs...)
```

ネットワーク `ntw` に単一のユーザーを追加し、対応する `PropDict` を名前付き引数 `kwargs` で埋めます。

# 例

```julia-repl
julia> ntwᵖʷʳ = ntw()
julia> add_source!(ntwᵖʷʳ, node = 1,
                           ind  = [:EENS])
```
