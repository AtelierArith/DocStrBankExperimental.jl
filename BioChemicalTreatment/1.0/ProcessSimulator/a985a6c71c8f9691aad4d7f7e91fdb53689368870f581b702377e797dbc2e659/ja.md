```
FlowSeparator(state; n_out=2, name)
```

単一のフローを複数に分離するためのコンポーネントです。これは、1つの流入のみを持つ `FlowConnector` のエイリアスです。

フローを分割するための流量は、次のシステムによって提供される必要があります。例えば、[`FlowPump`](@ref) です。すべての流出に対して1つを除いて [`FlowPump`](@ref) を接続し、最後の1つは質量バランスによってすでに固定されます。

# パラメータ:

  * `states`: フロー内のコンポーネント
  * `n_out`: 流出の数、デフォルトは2

# コネクタ:

  * `inflow`: `FlowSeparator` の流入
  * `outflow_i`: `FlowSeparator` の i 番目の流出
