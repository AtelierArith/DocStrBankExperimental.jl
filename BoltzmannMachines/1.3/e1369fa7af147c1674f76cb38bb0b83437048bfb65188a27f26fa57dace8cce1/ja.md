```
monitored_fitrbm(x; ...)
```

この関数は `fitrbm` と同じトレーニング手順を実行しますが、モニタリングを容易にします：データセット `x` に対して RBM モデルをフィットさせ、トレーニング中にモニタリング結果を 1 つの `Monitor` オブジェクトに収集します。収集されたモニタリング結果とトレーニングされた RBM の両方が返されます。

# オプションのキーワード引数：

  * `monitoring`: 4 つの引数を受け取るモニタリング関数またはモニタリング関数のベクター：

    1. モニタリング関数の結果を収集するために使用される `Monitor` オブジェクト
    2. RBM
    3. エポック
    4. モニタリングに使用されるデータ。

    デフォルトでは、モニタリングは行われません。
  * `monitoringdata`: モニタリングに使用され、`monitoring` 関数に渡されるデータを含む `DataDict`。デフォルトでは、トレーニングデータ `x` がモニタリングに使用されます。
  * その他の指定されたキーワード引数は単に `fitrbm` に渡されます。詳細については、そちらのドキュメントを参照してください。

# 例：

```
using Random; Random.seed!(0)
xtrain, xtest = splitdata(barsandstripes(100, 4), 0.3)
monitor, rbm = monitored_fitrbm(xtrain;
    monitoring = [monitorreconstructionerror!, monitorexactloglikelihood!],
    monitoringdata = DataDict("Training data" => xtrain, "Test data" => xtest),
    # `fitrbm` のためのいくつかの引数：
    nhidden = 10, learningrate = 0.002, epochs = 200)
using BoltzmannMachinesPlots
plotevaluation(monitor, monitorreconstructionerror)
plotevaluation(monitor, monitorexactloglikelihood)
```
