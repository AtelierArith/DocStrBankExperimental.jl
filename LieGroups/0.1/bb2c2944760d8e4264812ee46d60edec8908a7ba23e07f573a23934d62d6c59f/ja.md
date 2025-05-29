```
Identity{O<:AbstractGroupOperation}
```

群の単位元 $e ∈ \mathcal G$ を [`AbstractLieGroup`](@ref) $\mathcal G$ 上のタイプ `O` の [`AbstractGroupOperation`](@ref) で表現します。

点がその手元の群に無関係であるという哲学に似て、単位元は自分が属する群 $\mathcal G$ を保持しません。しかし、使用される [`AbstractGroupOperation`](@ref) のタイプに依存します。

対応する [`AbstractManifoldPoint`](@extref `ManifoldsBase.AbstractManifoldPoint`) または配列表現を取得する方法については、[`identity_element`](@ref) も参照してください。

# コンストラクタ

```
Identity(::AbstractLieGroup{𝔽,O}) where {𝔽,O<:AbstractGroupOperation}
Identity(o::AbstractGroupOperation)
Identity(::Type{AbstractGroupOperation})
```

対応するサブタイプ `O<:`[`AbstractGroupOperation`](@ref) の単位元を作成します。
