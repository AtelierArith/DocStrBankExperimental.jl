```
subfields(L::SimpleNumField) -> Vector{Tuple{NumField, Map}}
```

単純拡張 $L/K$ が与えられたとき、$K$ を含む $L$ のすべての部分体を、単純拡張 $k$ と埋め込み $\iota k \to K$ からなるタプル $(k, \iota)$ として返します。
