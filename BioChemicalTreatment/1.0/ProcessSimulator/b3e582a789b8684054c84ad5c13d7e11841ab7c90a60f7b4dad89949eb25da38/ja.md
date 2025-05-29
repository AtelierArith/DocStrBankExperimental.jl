```
FlowUnifier(state; n_in=2, name)
```

複数のフローを単一のフローに統合するためのコンポーネントです。これは、1つの流出のみを持つ `FlowConnector` のエイリアスです。

# パラメータ:

  * `states`: フロー内のコンポーネント
  * `n_in`: 流入の数、デフォルトは2

# コネクタ:

  * `inflow_i`: `FlowUnifier` の i 番目の流入
  * `outflow`: `FlowUnifier` の流出
