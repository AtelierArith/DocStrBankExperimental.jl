このドキュメントは、あなたがアクセスできるものを理解するのに役立つはずです。

  * "dx" と "dy" は x および y の制限微分です
  * "img_arr" はすべてのフレームの生データです
  * "red_zstack" は画像配列の赤チャネルです
  * "grn_zstack" は画像配列の緑チャネルです
  * "red*zproj" と "grn*zproj" は赤と緑の z 投影（平均関数を使用して取得）です
  * "red*img" と "grn*img" はそれらの z 投影を RGB{Float32} 画像にしたものです
  * "composite_img" は赤と緑の画像の合成です
  * "red*trace" と "grn*trace" はフレームごとの平均蛍光のトレースです
  * "dff*red*zstack" はローリング平均を用いて取得したデルタ f/f (f0-f)/f です
  * "dff*grn*zstack" はトレースの全体平均を使用して取得した dff です
  * "dff*red*comp*zstack" と "dff*grn*comp*zstack" は RGB{Float32} バージョンです
  * "dff*composite*zstack" は合成です
  * "dff*red*zproj" と "dff*grn*zproj" は dff 画像の zstack 投影です
  * "dff*red*img" と "dff*grn*img" は赤と緑の z 投影の画像バージョンです
  * "dff*composite*img" は赤と緑の画像の合成です
  * "dff*red*trace" と "dff*grn*trace" はトレースバージョンです
  * "pks*vals" は dff*green_trace の最大ピークと谷です
  * "grn*row*sums" はすべての緑セクション行の合計です
  * "grn*sect*arr" と "red*sect*arr" はピーク検出の結果として形成された配列です
