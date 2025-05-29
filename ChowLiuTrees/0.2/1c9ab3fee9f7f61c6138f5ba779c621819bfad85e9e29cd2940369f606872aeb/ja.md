Chow Liu Tree(s)を学習します。`train_x`がある場所に基づいてCPU/GPUで実行されます。

引数:

  * `train_x`: トレーニングデータ。GPUを使用したい場合は、この`CuArray(train_x)`を呼び出す前にGPUに移動してください。

キーワード引数:

  * `num_trees=1`: 学習したい木の数。
  * `dropout_prob=0.0`: 最大スパニングツリーを学習する際に、確率`dropout_prob`でエッジを削除します。
  * `weights=nothing`: サンプルの重み。`nothing`の場合、重みはすべて1です。
  * `pseudocount=0.0`: すべてのカテゴリに分散した合計の擬似カウントを追加します。
  * `Float=Float64`: 精度。`train_x`が大きい場合は`Float32`の方が速いです。
