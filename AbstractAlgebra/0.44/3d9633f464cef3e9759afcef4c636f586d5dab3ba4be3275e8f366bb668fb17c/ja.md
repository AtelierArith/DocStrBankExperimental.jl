```
comm(g::T, h::T, k::T...) where {T <: GroupElem}
```

左結合の反復コミュテータ $[[g, h], ...]$ を返します。ここで、$[g, h] = g^{-1} h^{-1} g h$ です。
