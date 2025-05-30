```
gaussiansmooth3d(image)

gaussiansmooth3d(image, sigma=[5,5,5];
    mask=nothing,
    nbox=ifelse(isnothing(mask), 3, 6), 
    weight=nothing, dims=1:min(ndims(image),3), 
    boxsizes=getboxsizes.(sigma, nbox),
    padding=false
    )
```

`image`に対してガウス平滑化を行い、`sigma`はガウスの標準偏差として使用されます。各次元で`nbox`回の移動平均フィルタを適用することによって実現されます。`sigma`の長さと平滑化される`dims`の長さは一致する必要があります。（デフォルトは`3`）

オプション引数：

  * `mask`: マスクを使用して欠損値を補間または外挿することによって平滑化を行うことができます。
  * `nbox`: ボックスの適用回数。通常の平滑化の場合はデフォルトで`3`、マスク付き平滑化の場合は`6`です。
  * `weight`: 重み付き平滑化を適用します。重み付きまたはマスク付きの平滑化のいずれかを実行できます。
  * `dims`: どの次元を平滑化するかを指定します。他の次元を手動でループすることに対応します。
  * `boxizes`: 提供されたsigmaを使用せずにボックスサイズを手動で指定します。`length(boxsizes)==length(dims) && length(boxsizes[1])==nbox`
  * `padding`: `true`の場合、平滑化の前に画像がゼロでパディングされ、平滑化後にパディングが削除されます。
