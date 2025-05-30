```
Resampler(matrix; max_resolution=automatic, method=Interpolations.Linear(), update_while_button_pressed=false)
```

大きな画像/ヒートマップを表示するために `heatmap` で使用できるリサンプリングタイプを作成します。渡されるのは、Interpolations.jl の補間インターフェースとして `array(linrange, linrange)` をサポートする任意の配列です。この配列がこれをサポートしていない場合、次のように補間オブジェクトに変換されます: `Interpolations.interpolate(data, Interpolations.BSpline(method))`。

  * `max_resolution` は、画面のフル解像度を使用するために `automatic` に設定するか、希望する解像度のタプル/整数に設定できます。
  * `method` は使用される補間方法で、デフォルトは `Interpolations.Linear()` です。
  * `update_while_button_pressed` は、マウスボタンが押されている間にヒートマップを更新します。ズーム/パンに便利です。例えば、WGLMakie でドラッグ中に更新を避けるために false に設定します。
  * `lowres_background` は、高解像度画像が計算されている間、常に低解像度の背景を表示します。
