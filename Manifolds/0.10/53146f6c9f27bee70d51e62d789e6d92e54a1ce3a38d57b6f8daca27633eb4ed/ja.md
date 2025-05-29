```
compose(G::AbstractDecoratorManifold, p, q)
```

要素 $p,q ∈ \mathcal{G}$ を群演算 $p \circ q$ を使用して合成します。

新しい群多様体で合成を実装するには、代わりに `_compose` をオーバーロードしてください。そうすることで、[`Identity`](@ref) 引数を持つメソッドが曖昧にならないようにします。
