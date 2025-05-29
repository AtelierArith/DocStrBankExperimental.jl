```
getball([T, ] x::ArbOrRef)
```

ボールの中心点 `m` と半径 `r` を含むタプル `(m::Arf, r::Mag)` を返します。`T` が指定されている場合、`m` と `r` の両方をこの型に変換します。`Arf` と `Arb` をサポートしています。

また、[`setball`](@ref) と [`getinterval`](@ref) も参照してください。
