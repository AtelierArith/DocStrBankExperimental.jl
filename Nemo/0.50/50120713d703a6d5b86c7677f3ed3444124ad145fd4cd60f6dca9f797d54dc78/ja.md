```
kronecker_symbol(x::ZZRingElem, y::ZZRingElem)
kronecker_symbol(x::Int, y::Int)
```

Kronecker記号$\left(\frac{x}{y}\right)$の値を返します。定義はHenri Cohenの著書「A Course in Computational Algebraic Number Theory」の定義1.4.8に従います。
