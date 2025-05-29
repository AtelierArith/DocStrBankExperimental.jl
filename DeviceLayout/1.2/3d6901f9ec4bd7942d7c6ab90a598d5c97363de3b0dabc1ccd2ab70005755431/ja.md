```
aref(x, c::AbstractRange, r::AbstractRange; kwargs...)
```

範囲に基づいて `ArrayReference` を構築します（おそらく `LinSpace` または `FloatRange`）。`c` は列の座標を指定し、`r` は行の座標を指定します。`c` と `r` のペアは、繰り返されるセルの起点を指定します。したがって、範囲の極値は結果として得られる `ArrayReference` のバウンディングボックスの極値を指定するわけではなく、注意が必要です。

キーワード引数は x 反射、拡大率、回転を指定し、同義語が許可されています：

  * X 反射: `:xrefl`, `:xreflection`, `:refl`, `:reflect`, `:xreflect`, `:xmirror`, `:mirror`
  * 拡大: `:mag`, `:magnification`, `:magnify`, `:zoom`, `:scale`
  * 回転: `:rot`, `:rotation`, `:rotate`, `:angle`

```
