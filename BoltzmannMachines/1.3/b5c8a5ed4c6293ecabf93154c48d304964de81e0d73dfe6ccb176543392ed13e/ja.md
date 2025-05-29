```
monitored_stackrbms(x; ...)
```

この関数は `stackrbms` と同じトレーニング手順を実行しますが、モニタリングを容易にします：データセット `x` を最初の層への入力として使用して RBM のスタックをトレーニングし、トレーニング中にすべてのモニタリング結果を `Monitor` のベクターに収集します。これには各 RBM 層の要素が含まれます。（分割された層の要素は再びベクターであり、各パーティションの要素が含まれます。）収集されたモニタリング結果とトレーニングされた RBM のスタックの両方が返されます。

# オプションのキーワード引数：

  * `monitoring`: 4 つの引数を受け取るモニタリング関数またはモニタリング関数のベクター：

    1. モニタリング関数の結果を収集するために使用される `Monitor` オブジェクト
    2. RBM
    3. エポック
    4. モニタリングに使用されるデータ。

    デフォルトでは、モニタリングは行われません。
  * `monitoringdata`: モニタリングに使用されるデータを含む `DataDict`。最初の層では、データは直接 `monitoring` 関数に渡されます。高層のトレーニングをモニタリングするためには、データはまず下の層を通じて伝播されます。デフォルトでは、トレーニングデータ `x` がモニタリングに使用されます。
  * その他の指定されたキーワード引数は単に `stackrbms` に渡されます。詳細については、そちらのドキュメントを参照してください。

# 例：

```
using Random; Random.seed!(0)
xtrain, xtest = splitdata(barsandstripes(100, 4), 0.5)
monitors, rbm = monitored_stackrbms(xtrain;
    monitoring = monitorreconstructionerror!,
    monitoringdata = DataDict("Training data" => xtrain, "Test data" => xtest),
    # `stackrbms` のためのいくつかの引数：
    nhiddens = [4; 3], learningrate = 0.005, epochs = 100)
using BoltzmannMachinesPlots
plotevaluation(monitors[1]) # 最初の RBM のモニタリングを表示
plotevaluation(monitors[2]) # 2 番目の RBM のモニタリングを表示
```
