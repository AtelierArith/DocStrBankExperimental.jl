```
responseparents(o::CausalTable)
```

与えられた `CausalTable` オブジェクトから各応答変数の親を選択します。

# 引数

  * `o::CausalTable`: 各応答の親変数を抽出するための `CausalTable` オブジェクト。
  * `collape_parents::Bool`: 出力を単一の `CausalTable` オブジェクトにまとめるかどうかのオプションパラメータ。応答が1つだけの場合、またはすべての応答が同じ親を持つ場合に `true` に設定されます。デフォルトは `true` です。

# 戻り値

応答の原因のみを含む新しい `CausalTable`（単一の応答の場合、またはすべての応答が同じ原因のセットを共有する場合）。そうでない場合は、各応答の原因を含む `CausalTable` オブジェクトのベクター。
