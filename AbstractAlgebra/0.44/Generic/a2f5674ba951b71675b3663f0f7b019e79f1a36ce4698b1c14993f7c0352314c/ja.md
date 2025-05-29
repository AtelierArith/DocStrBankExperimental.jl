```
mul_karatsuba(a::Poly{T}, b::Poly{T}, cutoff::Int) where T <: RingElement
```

カラツバアルゴリズムを使用して、サイズが大体 `cutoff` より大きい問題に対して再帰的に $a \times b$ を返します。
