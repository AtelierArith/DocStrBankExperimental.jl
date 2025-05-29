```
hlines(arg; decorated=(...), xmin=NaN, xmax=NaN, percent=false, kwargs...)
```

水平線を1本または複数描画し、必要に応じて装飾を加えます。

  * `xmin` & `xmax`: 水平線の開始位置を `xmin` に、終了位置を `xmax` に制限します。
  * `percent`: true の場合、`xmin` と `xmax` は図の高さの割合として解釈されます。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    マップの境界フレームと軸の属性を設定します。
  * **J** | **proj** | **projection** :: [Type => String]

    マップの投影を選択します。デフォルトは15x10 cmの線形（非投影）マップです。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **W** | **pen** | **line_attrib** :: [Type => Str]

    水平線のペン属性を設定します。

例:

```
plot(rand(5,3))
hlines!([0.2, 0.6], pen=(1, :red), show=true)
```
