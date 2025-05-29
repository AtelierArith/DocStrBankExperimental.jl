```
scalar_matrix(R::NCRing, n::Int, a::NCRingElement)
scalar_matrix(n::Int, a::NCRingElement)
```

`R`上の$n \times n$行列を返し、主対角線上に`a`があり、それ以外はゼロです。`R`が指定されていない場合、`parent(a)`がデフォルトになります。
