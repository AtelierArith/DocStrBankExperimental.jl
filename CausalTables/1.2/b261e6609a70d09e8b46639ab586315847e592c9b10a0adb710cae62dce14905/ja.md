```
mediatorsmatrix(o::CausalTable; collapse_parents = true)
```

指定された `CausalTable` オブジェクトから治療変数の交絡因子を行列（または複数の治療-応答ペアが存在する場合は行列の行列）として出力します。

# 引数

  * `o::CausalTable`: 各治療-応答ペアの媒介変数を抽出するための `CausalTable` オブジェクト。
  * `collape_parents::Bool`: 出力を単一の `Matrix` オブジェクトにまとめるかどうかを示すオプションのパラメータ。治療-応答ペアが1つだけの場合、またはすべてのペアが同じ媒介変数のセットを共有する場合に `true` に設定されます。デフォルトは `true` です。

# 戻り値

交絡因子のみを含む行列。
