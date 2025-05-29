```
smithscatter(z; kwargs...)
```

スミスチャート上に点を散布します。

# 有効なキーワード:

  * `color`  マーカーの色を設定します。`? scatter`を参照してください。
  * `colormap = :viridis` 数値カラーのためにサンプリングされるカラーマップを設定します。
  * `marker = :rect` 散布マーカーを設定します。
  * `markersize = 9` マーカーのサイズを設定します。
  * `label = nothing`
  * `reflection = false`: 正規化インピーダンスか反射係数かを指定します。
  * `freq = Float64[]` 各表現値に関連付けられた周波数の配列。主に`DataInspector`によって使用されます。
