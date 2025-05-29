```
layer(m::Meta)
```

`m`によって指定されたレイヤー、`Symbol`として。

例えば、`layer(GDSMeta(1, 2))`は`:GDS1_2`であり、`layername(SemanticMeta(:base))`は`:base`です。
