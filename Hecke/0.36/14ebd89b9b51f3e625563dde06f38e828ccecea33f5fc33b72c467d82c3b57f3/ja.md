```
maximal_even_lattice(L::ZZLat, p::IntegerUnion) -> ZZLat
```

整数格 `L` と整数スケールを持つ素数 `p` が与えられたとき、$L_p$ が偶数である場合、`L` の上格 `M` を返します。`M` は `p` で最大の偶数であり、他のすべての場所で `L` と局所的に一致します。
