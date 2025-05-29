```
commutator(g::El, h::El, k::El...) where {El <: GroupElement}
```

左結合の反復交換子 $[[g, h], ...]$ を返します。ここで、$[g, h] = g^{-1} h^{-1} g h$ です。
