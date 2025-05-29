```
Identity{O<:AbstractGroupOperation}
```

リー群 $\mathcal G$ 上の群の単位元 $e ∈ \mathcal{G}$ を、タイプ `O` の [`AbstractGroupOperation`](@ref) で表現します。

点が手元の群に対して無関心であるという哲学に似て、単位元は自分が属する群 `g` を保存しません。しかし、使用される [`AbstractGroupOperation`](@ref) のタイプに依存します。

対応する [`AbstractManifoldPoint`](@extref `ManifoldsBase.AbstractManifoldPoint`) または配列表現を取得する方法については、[`identity_element`](@ref) も参照してください。

# コンストラクタ

```
Identity(G::AbstractDecoratorManifold{𝔽})
Identity(o::O)
Identity(::Type{O})
```

対応するサブタイプ `O<:`[`AbstractGroupOperation`](@ref) の単位元を作成します。
