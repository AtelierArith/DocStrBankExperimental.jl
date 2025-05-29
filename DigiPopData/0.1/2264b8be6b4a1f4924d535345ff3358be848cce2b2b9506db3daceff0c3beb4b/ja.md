```
get_loss(simulated::DataFrame, metric_bindings::Vector{MetricBinding}) -> Float64
```

与えられたメトリックバインディングのセットとシミュレートされたDataFrameに対して損失を計算します。この関数はメトリックバインディングを反復処理し、各バインディングで指定されたシナリオとエンドポイントに基づいてシミュレートされたDataFrameから関連データを選択します。その後、メトリックで定義された`mismatch`関数を使用して損失を計算します。

## 引数

  * `simulated::DataFrame`: シミュレートされたデータを含むDataFrame。
  * `metric_bindings::Vector{MetricBinding}`: 各メトリック、シナリオ、およびエンドポイントを含む`MetricBinding`オブジェクトのベクター。
