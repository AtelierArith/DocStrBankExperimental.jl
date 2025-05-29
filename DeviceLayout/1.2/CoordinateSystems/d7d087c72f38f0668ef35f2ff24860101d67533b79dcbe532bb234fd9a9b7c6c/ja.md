```
addarr!(
    c1::AbstractCoordinateSystem,
    c2::GeometryStructure,
    c::AbstractRange,
    r::AbstractRange;
    kwargs...
)
```

`c1`の参照リストに、範囲に基づいて`c2`に`ArrayReference`を追加します。

`c`は列座標を指定し、`r`は行を指定します。`c`と`r`のペアは、繰り返されるセルの起点を指定します。したがって、範囲の極値は結果として得られる`ArrayReference`のバウンディングボックスの極値を指定するわけではなく、注意が必要です。

キーワード引数は、x反射、拡大率、および回転を指定し、同義語が許可されています：

  * X反射: `:xrefl`, `:xreflection`, `:refl`, `:reflect`, `:xreflect`, `:xmirror`, `:mirror`
  * 拡大: `:mag`, `:magnification`, `:magnify`, `:zoom`, `:scale`
  * 回転: `:rot`, `:rotation`, `:rotate`, `:angle`
