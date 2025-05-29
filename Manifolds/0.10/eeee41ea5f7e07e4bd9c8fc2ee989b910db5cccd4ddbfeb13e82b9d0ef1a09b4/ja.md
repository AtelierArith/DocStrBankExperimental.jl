```
rand(::KendallsShapeSpace; vector_at=nothing)
```

`vector_at`が`nothing`の場合、埋め込み内でランダムな点を生成することによって、[`KendallsShapeSpace`](@ref)多様体`M`上のランダムな点`x`を返します。

`vector_at`が`nothing`でない場合、平均がゼロで標準偏差が`σ`の接空間からランダムなベクトルを返します。
