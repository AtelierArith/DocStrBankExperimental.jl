```
fitrbm(x; ...)
```

データセット `x` にRBMモデルをフィットさせ、確率的勾配降下法（SGD）とコントラストダイバージェンス（CD）を使用して返します。

# オプションのキーワード引数（重要度順）：

  * `rbmtype`: 訓練されるRBMのタイプ これは `AbstractRBM` のサブタイプでなければならず、デフォルトは `BernoulliRBM` です。
  * `nhidden`: 返されるRBMの隠れユニットの数
  * `epochs`: 訓練エポックの数
  * `learningrate`/`learningrates`: 重みとバイアスの学習率 これはすべてのエポックで使用される単一の値として指定することも、各エポックの値を含む `learningrates` のベクトルとして指定することもできます。デフォルトは0.005です。
  * `batchsize`: 確率的勾配降下法最適化アルゴリズムで1ステップを行うために使用されるサンプルの数。デフォルトは1です。
  * `pcd`: 永続的コントラストダイバージェンス（PCD）を使用するかどうかを示します（true、デフォルト）またはトレーニングサンプルでギブスチェーンを初期化する単純なCD（false）
  * `cdsteps`: （永続的）コントラストダイバージェンスのためのギブスサンプリングステップの数、デフォルトは1
  * `monitoring`: 各訓練エポックの後に実行される関数。RBMとエポックを引数として取ります。監視の別の方法については `monitored_fitrbm` も参照してください。
  * `categories`: `rbmtype = Softmax0BernoulliRBM` の場合のみ関連します。すべての変数が同じ数のカテゴリを持つ場合は `Int` として、i番目のカテゴリ変数のi番目のエントリにおけるカテゴリの数として `Vector{Int}` として指定します。
  * `upfactor`, `downfactor`: この関数がDBMの一部の事前訓練に使用される場合、RBMの重みを因子で乗算する必要があります。
  * `sdlearningrate`/`sdlearningrates`: `GaussianBernoulliRBM` または `GaussianBernoulliRBM2` を訓練する場合の標準偏差の学習率。その他のタイプのRBMには無視されます。通常、重みの学習率よりもはるかに小さくする必要があります。デフォルトは0.0で、これは標準偏差が学習されないことを意味します。
  * `startrbm`: 指定されたRBMのパラメータで訓練を開始します。この引数が指定されると、`nhidden` と `rbmtype` は無視されます。
  * `optimizer`/`optimizers`: `AbstractOptimizer` 型のオブジェクトまたは各エポックのためのそれらのベクトル。指定された場合、最適化は指定されたオプティマイザタイプによって実装された通りに行われます。デフォルトでは、`learningrate`/`learningrates` と `sdlearningrate`/`sdlearningrates` を使用した `LoglikelihoodOptimizer` が使用されます。他のタイプのオプティマイザについては、`optimizer` で学習率を指定する必要があります。独自のオプティマイザを書く方法についての詳細は `AbstractOptimizer` を参照してください。

また、訓練の便利な監視のために `monitored_fitrbm` も参照してください。
