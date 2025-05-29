```
Chain(rules...)
Chain(rules::Tuple)
```

`Chain`は、グリッドからの中間読み取りや書き込みなしで、ルールを一つの処理ステップで完了させるためにルールを連鎖させることを可能にします。

特に、すべての`applyrule`メソッドに`@inline`を使用する場合、単一の関数呼び出しにまとめてコンパイルされる可能性があります。`Chain`は、すべての[`CellRule`](@ref)または[`NeighborhoodRule`](@ref)の後に[`CellRule`](@ref)を保持できます。

[`SetRule`](@ref)は戻り値を持たないため、`Chain`では使用できません。

![Chain rule diagram](https://raw.githubusercontent.com/cesaraustralia/DynamicGrids.jl/media/Chain.png)
