KuramotoSivashinsky1Dデータセットを作成します。サイズはn*pixels x n*timeの画像で、以下の引数が必要です。

  * split: :trainまたは:test
  * f: 希望するデータの割合
  * Tx: 浮動小数点型。データセットはFloat32を使用して作成されました。
  * n_pixels: 空間次元のノード数                      現在は128のみがサポートされています。
  * n_time: 2d ``images"を作成する際に使用する時間サンプルの数。
