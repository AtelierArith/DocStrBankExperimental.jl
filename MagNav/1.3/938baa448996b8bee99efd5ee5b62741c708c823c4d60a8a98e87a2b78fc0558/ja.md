```
vector_fft(map_map::Matrix, dx, dy, D, I)
```

ポテンシャルフィールド（すなわち、磁気異常フィールド）マップのベクトル成分を傾斜角と傾斜を使用して取得します。

**引数:**

  * `map_map`: `ny` x `nx` 2D グリッドマップデータ
  * `dx`:      x方向マップステップサイズ [m]
  * `dy`:      y方向マップステップサイズ [m]
  * `D`:       マップの傾斜角（地球コアフィールド） [rad]
  * `I`:       マップの傾斜（地球コアフィールド） [rad]

**戻り値:**

  * `Bx, By, Bz`: マップのベクトル成分
