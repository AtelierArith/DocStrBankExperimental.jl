```
inner(a::MultiValue{S}, b::MultiValue{S}) -> scalar
a ⊙ b
```

二つのテンソルの内積、すなわち各インデックスに沿った完全な収束です。`a` と `b` のサイズ `S` は一致している必要があります。
