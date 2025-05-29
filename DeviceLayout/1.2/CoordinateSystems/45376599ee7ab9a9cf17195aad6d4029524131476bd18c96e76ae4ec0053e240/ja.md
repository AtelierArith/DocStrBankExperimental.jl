```
addref!(c1::AbstractCoordinateSystem{T},
    c2::GeometryStructure,
    origin=zero(Point{T});
    kwargs...)
```

`c1`の参照リストに`c2`への参照を追加します。

`c2`への参照は`origin`を持ち、x反射、拡大率、回転はキーワード引数によって設定されます。

これらのキーワードには同義語が受け入れられます：

  * X反射: `:xrefl`, `:xreflection`, `:refl`, `:reflect`, `:xreflect`, `:xmirror`, `:mirror`
  * 拡大: `:mag`, `:magnification`, `:magnify`, `:zoom`, `:scale`
  * 回転: `:rot`, `:rotation`, `:rotate`, `:angle`
