```
scalar_matrix(R::NCRing, n::Int, a::NCRingElement)
scalar_matrix(n::Int, a::NCRingElement)
```

`R`が指定されていない場合、`a`の親がデフォルトとして使用されます。主対角線に`a`があり、それ以外はゼロの$n \times n$行列を返します。
