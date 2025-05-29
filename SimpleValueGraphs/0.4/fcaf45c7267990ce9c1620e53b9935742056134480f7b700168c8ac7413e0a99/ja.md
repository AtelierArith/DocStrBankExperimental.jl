```
ValGraph{V, V_VALS, E_VALS}(
    g::SimpleGraph;
    vertexval_init,
    edgeval_init,
    graphvals=()
)
ValGraph{V = eltype(g)}(
    g::SimpleGraph;
    vertexval_types=(),
    edgeval_types=(),
    vertexval_init,
    edgeval_init,
    graphvals=()
)
```

`g`と同じ構造の`ValGraph`を構築します。

# 引数

  * `g`: `Graphs.SimpleGraph`

# キーワード

  * `vertexval_init`: このグラフの頂点値をどのように初期化するか。関数`v -> (values...)`または`undef`のいずれかで指定できます。このグラフに頂点値がない場合は省略できます。
  * `edgeval_init`: このグラフの辺値をどのように初期化するか。関数`(s,d) -> (values...)`または`undef`のいずれかで指定できます。このグラフに辺値がない場合は省略できます。
  * `vertexval_types`: 型の`Tuple`または`NamedTuple`。
  * `edgeval_types`: 型の`Tuple`または`NamedTuple`。
  * `grapvals`: グラフ値の`Tuple`または`NamedTuple`。

# パラメータ

  * `V` このグラフの頂点のeltype。省略した場合は`eltype(g)`。
  * `V_VALS` 頂点値の型（`Tuple`または`NamedTuple`型）。`vertexval_init`キーワード引数で指定することもできます。
  * `E_VALS` 辺値の型（`Tuple`または`NamedTuple`型）。`edgeval_init`キーワード引数で指定することもできます。
