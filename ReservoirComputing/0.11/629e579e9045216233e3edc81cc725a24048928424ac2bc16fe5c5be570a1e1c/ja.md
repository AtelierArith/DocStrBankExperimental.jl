```
GRU(;activation_function=[NNlib.sigmoid, NNlib.sigmoid, tanh],
    inner_layer = fill(DenseLayer(), 2),
    reservoir = fill(RandSparseReservoir(), 2),
    bias = fill(DenseLayer(), 2),
    variant = FullyGated())
```

エコー状態ネットワーク（`ESN`）のためのゲート付き再帰ユニット（GRU）レザーバドライバを返します。このドライバはGRUアーキテクチャに基づいています [^Cho2014]。

# 引数

  * `activation_function`: GRU層のための活性化関数の配列。デフォルトでは、更新ゲートとリセットゲートにはシグモイド活性化関数、隠れ状態にはtanhを使用します。
  * `inner_layer`: GRUアーキテクチャで使用される内部層の配列。デフォルトでは、2つの密な層を使用します。
  * `reservoir`: レザーバ層の配列。デフォルトでは、2つのランダムスパースレザーバを使用します。
  * `bias`: GRUのためのバイアス層の配列。デフォルトでは、2つの密な層を使用します。
  * `variant`: 使用するGRUのバリアント。デフォルトでは、「FullyGated」バリアントを使用します。

[^Cho2014]: Cho, Kyunghyun, et al. "*Learning phrase representations using RNN encoder-decoder for statistical machine translation.*" arXiv preprint arXiv:1406.1078 (2014).
