```
zoom_lines!(ax1, ax2; strokewidth=1.5, strokecolor=:black, color=(:black, 0), rectattrs=(;), lineattrs=(;))
```

描画内容:

  * 他の軸の小さい範囲を囲む大きい範囲を持つ軸上に矩形を描画します;
  * 矩形の対応するコーナーを結ぶ線を描画します。

矩形と線の両方で共有される一般的な属性は `strokewidth` と `strokecolor` です。 `rectattrs` と `lineattrs` は、必要に応じて矩形と線の属性を個別に上書きするために使用されます。
