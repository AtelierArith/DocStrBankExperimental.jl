add*volcano!(     Phases, Temp, Grid::CartData;     volcanic*phase,     center,     height,     radius,     crater,     base,     background,     T, )

火山の地形（円錐と切り取られた円錐）を追加します。

# パラメータ

  * Phases - グリッドと一致するフェーズ配列
  * Temp - グリッドと一致する温度配列
  * Grid - CartData

# オプションのパラメータ

  * volcanic_phase - 火山のフェーズ番号
  * center - 火山の中心のx座標とy座標
  * height - 火山の高さ
  * radius - 火山の半径
  * T - 火山の温度構造
  * crater - これにより切り取られた円錐が作成され、オプションは平らな頂部の半径を定義します
  * base - これにより火山の周りの平坦な地形が設定されます
  * background - これにより地形を読み込み、火山の上にのみ追加することができます（異なる傾斜を持つ火山を得るためにいくつかの円錐を重ねることも可能です）
