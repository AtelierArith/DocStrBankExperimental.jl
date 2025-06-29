```
DeepESN(train_data, in_size, res_size; kwargs...)
```

シーケンシャルデータを層状のリザーバーアーキテクチャを通じて処理するためのディープエコー状態ネットワーク（ESN）モデルを構築します。このコンストラクタは、複数のリザーバー層によって提供される深さによって強化されたESNの動的メモリと時間処理能力の恩恵を受けるディープラーニングモデルの作成を可能にします。

# パラメータ

  * `train_data`: ESNに使用されるトレーニングデータセット。これは、適用可能な場合にシーケンシャルデータとして構造化されるべきです。
  * `in_size`: 入力層のサイズ、すなわちESNへの入力ユニットの数。
  * `res_size`: 各リザーバーのサイズ、すなわちESNの各隠れ層のニューロンの数。

# オプションのキーワード引数

  * `depth`: ディープESNのリザーバー層の数。デフォルトは2です。
  * `input_layer`: 各層の入力行列を初期化するための関数または関数の配列。デフォルトは各層の`scaled_rand`です。
  * `bias`: 各層のバイアスベクトルを初期化するための関数または関数の配列。デフォルトは各層の`zeros32`です。
  * `reservoir`: 各層のリザーバー行列を初期化するための関数または関数の配列。デフォルトは各層の`rand_sparse`です。
  * `reservoir_driver`: リザーバーの駆動システム。デフォルトはRNNモデルです。
  * `nla_type`: リザーバーで使用される非線形活性化のタイプ。デフォルトは`NLADefault()`です。
  * `states_type`: ESNで使用される状態のタイプを定義します（例：標準状態）。デフォルトは`StandardStates()`です。
  * `washout`: ESNのトレーニングフェーズで破棄される初期タイムステップの数。デフォルトは0です。
  * `rng`: 重みを初期化するために使用される乱数生成器。デフォルトは`Utils.default_rng()`です。
  * `matrix_type`: トレーニングデータを保存するために使用される行列のタイプ。デフォルトは`train_data`から推測されます。

# 例

```julia
train_data = rand(Float32, 3, 100)

# 特定のパラメータでDeepESNを作成
deepESN = DeepESN(train_data, 3, 100; depth=3, washout=100)
```
