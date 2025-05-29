```
plot(f::Function, xmin::Number, xmax::Number, ymin::Number, ymax::Number,
     elements::ElementOrFunction...; mapping...)
```

`f`の2D関数または式の輪郭をプロットします。関数の計算には[`Stat.contour`](@ref)を使用します。詳細は[`Geom.contour`](@ref)を参照してください。
