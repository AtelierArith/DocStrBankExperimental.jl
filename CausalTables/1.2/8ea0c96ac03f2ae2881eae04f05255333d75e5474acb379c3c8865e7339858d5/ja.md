```
confounders(o::CausalTable; collapse_parents = true)
```

与えられた `CausalTable` オブジェクトから各応答-治療ペアの交絡因子を選択します。

# 引数

  * `o::CausalTable`: 各治療-応答ペアの交絡因子変数を抽出するための `CausalTable` オブジェクト。
  * `collape_parents::Bool`: オプションのパラメータで、治療-応答ペアが1つだけの場合、またはすべてのペアが同じ交絡因子のセットを共有する場合に出力を単一の `CausalTable` オブジェクトにまとめるかどうか。デフォルトは `true`。

# 戻り値

交絡因子のみを含む新しい `CausalTable`（単一の応答の場合、またはすべての応答が同じ原因のセットを共有する場合）。そうでない場合は、各治療-応答ペアの交絡因子を含む CausalTable オブジェクトの行列で、行は応答を、列は治療を表します。
