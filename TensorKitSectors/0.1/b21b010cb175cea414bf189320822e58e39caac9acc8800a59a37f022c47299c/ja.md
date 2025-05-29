```
Nsymbol(a::I, b::I, c::I) where {I<:Sector} -> Integer
```

`a ⊗ b`の融合積において`c`が出現する回数を表す`Integer`を返します。`FusionStyle(I) == UniqueFusion()`または`SimpleFusion()`の場合は`Bool`になることがあります。
