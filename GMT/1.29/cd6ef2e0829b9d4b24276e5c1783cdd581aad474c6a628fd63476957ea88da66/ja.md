```
vlines(arg; decorated=(...), ymin=NaN, ymax=NaN, percent=false, kwargs...)
```

1本または複数の垂直線を描画し、必要に応じて装飾を追加します。

  * `ymin` & `ymax`: 垂直線を`ymin`から開始し、`ymax`で終了するように制限します。
  * `percent`: trueの場合、`xmin` & `xmax`は図の幅の割合として解釈されます。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **W** | **pen** | **line_attrib** :: [Type => Str]

    水平線のペン属性を設定します。

例:

```
plot(rand(5,3), region=[0,1,0,1])
vlines!([0.2, 0.6], pen=(1, :red), show=true)
```
