```
monitored_fitdbm(x; ...)
```

この関数は `fitdbm` と同じトレーニング手順を実行しますが、モニタリングを容易にします：データセット `x` に対して DBM モデルを貪欲なレイヤーごとの事前トレーニングとその後のファインチューニングを使用してフィットし、トレーニング中にすべてのモニタリング結果を収集します。モニタリング結果は `Monitor` のベクターに格納され、各 RBM レイヤーの要素と最後の要素としてファインチューニングのモニタリング結果が含まれます。（分割されたレイヤーの事前トレーニングからのモニタリング要素は再びベクターであり、各パーティションの要素が含まれます。）収集されたモニタリング結果とトレーニングされた DBM の両方が返されます。

参照： `monitored_stackrbms`, `monitored_traindbm!`

# オプションのキーワード引数：

  * `monitoring`: ファインチューニングに使用されます。4つの引数を受け取るモニタリング関数またはモニタリング関数のベクター：

    1. モニタリング関数の結果を収集するために使用される `Monitor` オブジェクト
    2. DBM
    3. エポック
    4. モニタリングに使用されるデータ。

    デフォルトでは、ファインチューニングのモニタリングはありません。
  * `monitoringdata`: モニタリングに使用されるデータを含む `DataDict`。最初のレイヤーの事前トレーニングとファインチューニングのために、データは直接 `monitoring` 関数に渡されます。高次の RBM レイヤーの事前トレーニングをモニタリングするために、データはまず下のレイヤーを通じて伝播されます。デフォルトでは、トレーニングデータ `x` がモニタリングに使用されます。
  * `monitoringpretraining`: 事前トレーニングに使用されます。`monitoring` のような4引数の関数ですが、2番目の引数として RBM を受け取ります。デフォルトでは、事前トレーニングのモニタリングはありません。
  * `monitoringdatapretraining`: 事前トレーニングのみに使用されるモニタリングデータ。デフォルトは `monitoringdata` です。
  * その他の指定されたキーワード引数は単に `fitdbm` に渡されます。詳細については、そちらのドキュメントを参照してください。

# 例：

```
using Random; Random.seed!(1)
xtrain, xtest = splitdata(barsandstripes(100, 4), 0.5)
monitors, dbm = monitored_fitdbm(xtrain;
    monitoringpretraining = monitorreconstructionerror!,
    monitoring = monitorlogproblowerbound!,
    monitoringdata = DataDict("Training data" => xtrain, "Test data" => xtest),
    # `fitdbm` のためのいくつかの引数：
    nhiddens = [4; 3], learningratepretraining = 0.01,
    learningrate = 0.05, epochspretraining = 100, epochs = 50)
using BoltzmannMachinesPlots
plotevaluation(monitors[1]) # 最初の RBM のモニタリングを表示
plotevaluation(monitors[2]) # 2番目の RBM のモニタリングを表示
plotevaluation(monitors[3]) # ファインチューニングのモニタリングを表示
```
