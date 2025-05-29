```
primitivize(r::DirectPoint, cntr_or_sgnum::Union{Char, <:Integer}) --> r′::typeof(r)
```

入力点 `r` の座標が従来の基底にあるのに対し、原始基底に座標を持つ直接点 `r′` を返します。
