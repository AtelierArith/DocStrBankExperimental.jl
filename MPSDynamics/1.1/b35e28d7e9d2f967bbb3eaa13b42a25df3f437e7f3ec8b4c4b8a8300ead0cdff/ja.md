```
randmps(tree::Tree, physdims, Dmax::Int, T::Type{<:Number} = Float64)
```

ツリーによって与えられた構造と、`Dmax`で指定された最大ボンド次元を持つ、ランダムで右正規化されたツリーMPSを構築します。

局所ヒルベルト空間の次元は、`Dims{length(tree)}`型のphysdimsによって指定され、各サイトの次元を指定するか、`Int`型の場合は、すべてのサイトに同じ局所次元が使用されます。
