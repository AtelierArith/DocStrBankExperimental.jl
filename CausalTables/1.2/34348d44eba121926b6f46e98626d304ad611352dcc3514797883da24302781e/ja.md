```
treatmentparents(o::CausalTable)
```

与えられた `CausalTable` オブジェクトから各治療変数の親を選択します。

# 引数

  * `o::CausalTable`: 各治療の親変数を抽出するための `CausalTable` オブジェクト。
  * `collape_parents::Bool`: オプションのパラメータで、治療が1つだけの場合やすべての治療が同じ親を持つ場合に出力を単一の `CausalTable` オブジェクトにまとめるかどうか。デフォルトは `true`。

# 戻り値

治療の原因のみを含む新しい `CausalTable`（単一の治療の場合、またはすべての治療が同じ原因のセットを共有する場合）。そうでない場合は、各治療の原因を含む CausalTable オブジェクトのベクター。
