```
Layered <: Abstract

Layered(layers::Union{Stencil,Layered}...)
Layered(; layer_keywords...)
Layered(layers::Union{Tuple,NamedTuple})
```

一緒に使用できるステンシルの`Tuple`または`NamedTuple`。

`Layered`の`neighbors`は、各ステンシルレイヤーのイテレータのタプルを返します。
