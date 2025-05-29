```
map_border(map_map::Matrix, map_xx::Vector, map_yy::Vector;
           inner::Bool       = true,
           sort_border::Bool = false,
           return_ind::Bool  = false)
```

未填充のマップからマップの境界を取得します。

**引数:**

  * `map_map`:     `ny` x `nx` 2D グリッドマップデータ
  * `map_xx`:      `nx` マップの x 方向（経度）座標
  * `map_yy`:      `ny` マップの y 方向（緯度）座標
  * `inner`:       （オプション）true の場合、内側の境界を取得し、そうでない場合は外側の境界を取得
  * `sort_border`: （オプション）true の場合、境界データポイントを順次ソート
  * `return_ind`:  （オプション）true の場合、`ind` を返す

**戻り値:**

  * `yy`:  境界の y 方向（緯度）座標
  * `xx`:  境界の x 方向（経度）座標
  * `ind`: `return_ind = true` の場合、`map_map` 内の境界インデックスの `BitMatrix`
