```
monitored_traindbm!(dbm, x; ...)
```

この関数は `traindbm!` と同じトレーニング手順を実行しますが、モニタリングを容易にします：与えられた `dbm` をデータセット `x` でファインチューニングし、トレーニング中にモニタリング結果を1つの `Monitor` オブジェクトに収集します。収集されたモニタリング結果とトレーニングされた `dbm` の両方が返されます。

# オプションのキーワード引数：

  * `monitoring`: 4つの引数を受け取るモニタリング関数またはモニタリング関数のベクター：

    1. モニタリング関数の結果を収集するために使用される `Monitor` オブジェクト
    2. DBM
    3. エポック
    4. モニタリングに使用されるデータ。

    デフォルトでは、モニタリングは行われません。
  * `monitoringdata`: モニタリングに使用され、`monitoring` 関数に渡されるデータを含む `DataDict`。デフォルトでは、トレーニングデータ `x` がモニタリングに使用されます。
  * その他の指定されたキーワード引数は単に `traindbm!` に渡されます。詳細については、そちらのドキュメントを参照してください。

# 例：

```
using Random; Random.seed!(0)
xtrain, xtest = splitdata(barsandstripes(100, 4), 0.1)
dbm = stackrbms(xtrain; predbm = true, epochs = 20)
monitor, dbm = monitored_traindbm!(dbm, xtrain;
    monitoring = monitorlogproblowerbound!,
    monitoringdata = DataDict("Training data" => xtrain, "Test data" => xtest),
    # `traindbm!` のためのいくつかの引数：
    epochs = 100, learningrate = 0.1)
using BoltzmannMachinesPlots
plotevaluation(monitor)
```
