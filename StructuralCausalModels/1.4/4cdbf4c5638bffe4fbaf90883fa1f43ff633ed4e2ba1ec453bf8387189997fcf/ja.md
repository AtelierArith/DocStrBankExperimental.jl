# `set_dag_cov_matrix!`

DAGに関連付けられた共分散行列を設定または更新します

```julia
set_dag_cov_matrix!(d, cm; force)

```

### 必須引数

```julia
* `d::DAG`                                  : 以前に定義されたDAGオブジェクト 
* `cm::NamedArrayOrNothing`                 : NamedArray形式の共分散行列
)
```

### オプション引数

```julia
* `force=false`                             : dfの強制割り当て 
)
```

`force = true`オプションは、DAGに未観測ノードが含まれる場合に使用できます。

APIの一部であり、エクスポートされています。
