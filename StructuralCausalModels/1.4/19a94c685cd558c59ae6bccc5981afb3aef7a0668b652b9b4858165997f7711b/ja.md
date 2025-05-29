# `set_dag_df!`

DAGに関連付けられたDataframeを設定または更新します

```julia
set_dag_df!(d, df; force)

```

### 必須引数

```julia
* `d::DAG`                                  : 以前に定義されたDAGオブジェクト 
* `df::DataFrameOrNothing`                  : DAGに関連付けられたDataFrame
)
```

### オプション引数

```julia
* `force=false`                             : dfの強制割り当て 
)
```

`force = true`オプションは、DAGに未観測ノードが含まれる場合に使用できます。

APIの一部であり、エクスポートされています。
