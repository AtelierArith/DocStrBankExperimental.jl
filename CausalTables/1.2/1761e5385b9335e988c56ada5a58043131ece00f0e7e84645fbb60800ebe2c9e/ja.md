```
instrumentsmatrix(o::CausalTable; collapse_parents = true)
```

指定された `CausalTable` オブジェクトから治療変数のインスツルメントを行列（または複数の治療-反応ペアが存在する場合は行列の行列）として出力します。

# 引数

  * `o::CausalTable`: 各治療-反応ペアのインスツルメントを抽出するための `CausalTable` オブジェクト。
  * `collape_parents::Bool`: 出力を単一の `Matrix` オブジェクトにまとめるかどうかのオプションパラメータ。治療-反応ペアが1つだけの場合、またはすべてのペアが同じインスツルメントのセットを共有する場合に `true` に設定されます。デフォルトは `true` です。

# 戻り値

混乱因子のみを含む行列。
