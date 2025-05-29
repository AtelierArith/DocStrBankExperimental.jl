```
fitdbm(x; ...)
```

データセット `x` に (多峰性) DBM をフィットさせます。この手順は二つの部分から成ります。まず、RBM のスタックが貪欲な層ごとの方法で事前学習されます (詳細は `stackrbms(x)` を参照)。次に、すべての層の重みが一般的なボルツマンマシン学習手法を用いて共同で訓練されます (ファインチューニング、詳細は `traindbm!(dbm,x)` を参照)。

# オプションのキーワード引数 (重要度順):

  * `nhiddens`: DBM の隠れ層のノード数を定義するベクトル。デフォルト値は可視層と同じサイズの二つの隠れ層を指定します。
  * `epochs`: 共同訓練のための訓練エポック数、デフォルトは 10
  * `epochspretraining`: 事前学習のための訓練エポック数、デフォルトは `epochs`
  * `learningrate`: 事前学習のための学習率。減衰するファインチューニング学習率の初期値としても使用されます。
  * `learningratepretraining`: 事前学習のための学習率、デフォルトは `learningrate`
  * `learningratefinetuning`: ファインチューニングのための初期学習率。ファインチューニングの学習率はエポック数に応じて減衰し、`learningratefinetuning` または `learningrate` の指定された値から始まります。(詳細は `traindbm!` を参照。)
  * `learningratesfinetuning`: ファインチューニングのための学習率はデフォルトでエポック数に応じて減衰し、`learningrate` の値から始まります。(詳細は `traindbm!` を参照。) ファインチューニングの各エポックの学習率の値は、引数 `learningratesfinetuning` を介してベクトルとして指定できます。
  * `learningrates`: 非推奨、その他は `learningratesfinetuning` と同等
  * `batchsize`: 事前学習とファインチューニングのためのミニバッチ内のサンプル数。デフォルトでは、事前学習のためにバッチサイズ 1 が使用されます。ファインチューニングでは、デフォルトでミニバッチは使用されず、各エポックで勾配を計算するために完全なデータセットが使用されます。
  * `batchsizepretraining`: 事前学習のためのバッチサイズ、デフォルトは 1
  * `batchsizefinetuning`: ファインチューニングのためのバッチサイズ。デフォルトはデータセット内のサンプル数、すなわちミニバッチは使用されません。
  * `nparticles`: DBM の共同訓練中にサンプリングに使用される粒子の数、デフォルトは 100
  * `pretraining`: 層ごとの事前学習の引数は各層ごとに個別に指定できます。これは `TrainLayer` オブジェクトのベクトルを介して行います。(可能なパラメータの詳細な説明については、`TrainLayer` のヘルプを参照。) 訓練エポック数と学習率が層ごとに明示的に指定されていない場合、`epochspretraining`、`learningratepretraining` および `batchsizepretraining` の値が使用されます。
  * `monitoring`: `dbm` とエポック数を受け取り、何も返さない監視関数。ファインチューニングの監視に使用されます。より便利な監視方法については `monitored_fitdbm` も参照してください。
  * `monitoringdatapretraining`: 事前学習の監視に使用されるデータを含む `DataDict` (詳細は `stackrbms` の引数 `monitoringdata` を参照。)
  * `optimizer`/`optimizers`: ファインチューニングに使用されるオプティマイザまたは各エポックのオプティマイザのベクトル (詳細は `AbstractOptimizer` を参照)。
  * `optimizerpretraining`: 事前学習に使用されるオプティマイザ。デフォルトは `optimizer`。
