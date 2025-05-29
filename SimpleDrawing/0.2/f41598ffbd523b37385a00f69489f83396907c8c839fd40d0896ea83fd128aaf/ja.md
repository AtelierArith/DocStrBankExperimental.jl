`draw_vector` はベクトル（片方の端に矢印のある線分）を描画するために使用されます。バリエーションは次のとおりです：

  * `draw_vector(x,y)` は原点から `(x,y)` までのベクトルを描画します。
  * `draw_vector(x,y,basex,basey)` は `(basex,basey)` から `(basex+x,basey+y)` までのベクトルを描画します。
  * `draw_vector(z)` は原点から複素数値 `z` までのベクトルを描画します。
  * `draw_vector(z,basez)` は複素数位置 `basez` から `z+basez` までのベクトルを描画します。
