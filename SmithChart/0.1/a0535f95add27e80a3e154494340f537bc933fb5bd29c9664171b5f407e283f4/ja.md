```
smithplot(z; kwargs...)
```

スミスチャートに線をプロットします。

# 有効なキーワード:

  * `color`  マーカーの色を設定します。`? scatter`を参照してください。
  * `colormap = :viridis` 数値カラーのためにサンプリングされるカラーマップを設定します。
  * `linestyle = :rect` 線のパターンを設定します。例: :solid, :dot, :dashdot。
  * `line_width = 2.8` ピクセル単位で線の幅を設定します。
  * `label = nothing`
  * `reflection = false`: 正規化インピーダンスか反射係数かを指定します。
  * `freq = Float64[]` 各表現値に関連付けられた周波数の配列。主に`DataInspector`によって使用されます。
