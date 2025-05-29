transformedimagebounds

変換行列 H によって画像のコーナーがどこに変換されるかを見つけ、境界を返します。

```
Usage:  (minx, maxx, miny, maxy) = transformedimagebounds(img::Array, H::Array)
        (minx, maxx, miny, maxy) = transformedimagebounds(sze::Tuple, H::Array)

Arguments:   img - 画像を格納する配列または
             sze - 画像のサイズを示すタプル。
               H - 変換ホモグラフィー、3x3 行列。

Returns:
      minx, maxx - x, y 座標の範囲（列と行の座標の範囲）
      miny, maxy   変換された画像の範囲。

```
