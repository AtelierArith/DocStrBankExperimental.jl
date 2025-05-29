```
layer(f::Function, xmin::Number, xmax::Number, ymin::Number, ymax::Number,
      elements::ElementOrFunction...; mapping...) -> [Layers]
```

2D関数または式`f`の輪郭のレイヤーを作成します。関数の計算には[`Stat.contour`](@ref)を使用します。詳細は[`Geom.contour`](@ref)を参照してください。
