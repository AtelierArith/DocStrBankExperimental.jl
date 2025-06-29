```
add_gauss(X; clip=false[, σ=0.1, μ=0.0])
```

配列 `X` にガウスノイズ（標準偏差 `σ` と平均 `μ`）が追加されます。 `σ` と `μ` はガウスの標準偏差と平均を表すオプション引数です。キーワード引数 `clip` が提供されると、値は [0, 1] の範囲にクリップされます。もし `X` が RGB{Normed} または Gray{Normed} 画像であれば、値は自動的にクリップされ、キーワード `clip` は意味を持ちません。

もし `X<:Complex` の場合、`μ` と `σ` は実部と同様に虚部に適用されます。実部と虚部で異なる動作を持たせたい場合は、単に `μ` または `σ` を複素数にしてください。
