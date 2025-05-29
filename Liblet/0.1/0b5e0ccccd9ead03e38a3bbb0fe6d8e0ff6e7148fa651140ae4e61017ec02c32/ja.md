このタイプは[`Automaton`](@ref)遷移を表します。`from` 開始 *状態* と `to` 目的地 *状態*、および `label` を持っています。

```
Transition(from::Union{AbstractString, Iterable}, label::AbstractString, to::Union{AbstractString, Iterable})
```

与えられた状態に基づいて遷移を構築します。
