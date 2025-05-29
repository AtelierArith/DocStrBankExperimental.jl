# DAG

有向非巡回グラフ構造体

### 構造体

```julia
DAG(
* `name::AbstractString`                    : DAGオブジェクトの名前
* `d::OrderedDictOrNothing`                 : OrderedDictとしてのDAG定義
* `a::NamedArrayOrNothing`                  : 隣接行列
* `e::NamedArrayOrNothing`                  : エッジ行列
* `s::NamedArrayOrNothing`                  : 共分散行列
* `df::DataFrameOrNothing`                  : 変数の観測
* `vars::Vector{Symbol}`                    : DAG内の変数の名前
)
```

APIの一部、エクスポートされています。
