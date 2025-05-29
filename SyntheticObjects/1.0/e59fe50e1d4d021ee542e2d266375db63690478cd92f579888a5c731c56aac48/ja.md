```
draw_line!(arr, start, stop; thickness=0.5, intensity=one(eltype(arr)))
```

3D配列にガウスプロファイルを追加することで、線を描画します。

# 引数:

  * `arr::Array`: 線が追加される3D配列。
  * `start`: 線の開始点をタプルとして指定します。
  * `stop`: 線の停止点をタプルとして指定します。
  * `thickness`: 線の太さ。デフォルトは0.5です。
  * `intensity::Float64`: 線の強度。デフォルトは1.0です。
