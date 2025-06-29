```
constant(value) -> Node
constant(T, value) -> Node{T}
```

明示的に `value` を `TimeDag` 定数ノードにラップします。型に関係なく。

`T` が提供される場合、これは `value` の型のスーパタイプである [`value_type`](@ref) を持つノードの作成を可能にします。そうでなければ、定数ノードは常に `value` の具体的な型を使用します。

多くの場合、これは必要ありません。なぜなら、ノードを期待する多くの `TimeDag` 関数は、非ノード引数を自動的に定数ノードにラップするからです。

!!! warning
    もし `value` がすでにノードである場合、これはそれを追加のノードにラップします。これは非常におそらくあなたがしたいことではありません。

