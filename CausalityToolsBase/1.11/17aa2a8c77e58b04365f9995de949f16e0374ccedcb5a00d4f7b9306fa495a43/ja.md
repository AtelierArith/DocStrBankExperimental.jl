```
mutualinfo(pts, marginalinds_x, marginalinds_y, kernel::Kernel = GaussianKernel(); 
    b = 2, kwargs...)
```

カーネル密度推定器を使用して相互情報量を推定します。

## 引数

  * **`pts`**: 結合空間内の点。スカラーデータ系列 `X` と `Y` の間の相互情報量を計算する場合、点は2次元になります。より高次元の点を提供し、`marginalinds_x` と `marginalinds_y` を使用して考慮する周辺を示すことで、特定の座標軸間の相互情報量を計算することも可能です。
  * **`marginalinds_x`**: 最初の周辺のインデックス。
  * **`marginalinds_y`**: 2番目の周辺のインデックス。
  * **`kernel`**: 有効なカーネルのインスタンス。デフォルトは `BoxKernel()` です。

## キーワード引数

  * **`b`**: 対数の底で、情報の単位を決定します（例: `b = 2` は情報をビット単位で提供します）。
