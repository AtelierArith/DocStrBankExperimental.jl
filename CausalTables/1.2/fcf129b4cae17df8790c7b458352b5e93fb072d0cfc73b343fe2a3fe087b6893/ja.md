```
confoundersmatrix(o::CausalTable; collapse_parents = true)
```

指定された `CausalTable` オブジェクトから治療変数の交絡因子を行列（または複数の治療-反応ペアが存在する場合は行列の行列）として出力します。

# 引数

  * `o::CausalTable`: 各治療-反応ペアの交絡因子を抽出するための `CausalTable` オブジェクト。
  * `collape_parents::Bool`: 出力を単一の `Matrix` オブジェクトにまとめるかどうかを示すオプションのパラメータ。治療-反応ペアが1つだけの場合、またはすべてのペアが同じ交絡因子のセットを共有する場合に `true` に設定されます。デフォルトは `true` です。

# 戻り値

交絡因子のみを含む行列。
