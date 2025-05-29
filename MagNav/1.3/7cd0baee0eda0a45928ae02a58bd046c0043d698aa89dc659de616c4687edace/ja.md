```
get_nn_m(Nf::Int, Ny::Int = 1;
         hidden                = [8],
         activation::Function  = swish,
         final_bias::Bool      = true,
         skip_con::Bool        = false,
         model_type::Symbol    = :m1
         l_window::Int         = 5,
         tf_layer_type::Symbol = :postlayer,
         tf_norm_type::Symbol  = :batch,
         dropout_prob::Real    = 0.2,
         N_tf_head::Int        = 8,
         tf_gain::Real         = 1.0)
```

ニューラルネットワークモデルを取得します。隠れ層は0-3層有効ですが、`model_type = :m3w, :m3tf`の場合は1層または2層のみ有効です。

**引数:**

  * `Nf`:            入力（特徴）層の長さ
  * `Ny`:            （オプション）出力層の長さ
  * `hidden`:        （オプション）隠れ層とノード（例：2つの隠れ層、各8ノードの場合は`[8,8]`）
  * `activation`:    （オプション）活性化関数

      * `relu`  = 修正線形単位
      * `σ`     = シグモイド（ロジスティック関数）
      * `swish` = セルフゲーテッド
      * `tanh`  = 双曲線タンジェント
      * `plot_activation()`を実行して視覚化
  * `final_bias`:    （オプション）trueの場合、最終層のバイアスを含める
  * `skip_con`:      （オプション）trueの場合、スキップ接続を使用、`length(hidden)` == 1でなければならない
  * `model_type`:    （オプション）空気磁気補償モデルのタイプ
  * `l_window`:      （オプション）時間ウィンドウの長さ、`model_type = :m3w, :m3tf`のみに使用
  * `tf_layer_type`: （オプション）スキップ接続の前または後のトランスフォーマー正規化層 {`:prelayer`,`:postlayer`}、`model_type = :m3tf`のみに使用
  * `tf_norm_type`:  （オプション）トランスフォーマーエンコーダーの正規化 {`:batch`,`:layer`,`:none`}、`model_type = :m3tf`のみに使用
  * `dropout_prob`:  （オプション）ドロップアウト率、`model_type = :m3w, :m3tf`のみに使用
  * `N_tf_head`:     （オプション）アテンションヘッドの数、`model_type = :m3tf`のみに使用
  * `tf_gain`:       （オプション）重み初期化パラメータ、`model_type = :m3tf`のみに使用

**戻り値:**

  * `m`: ニューラルネットワークモデル
