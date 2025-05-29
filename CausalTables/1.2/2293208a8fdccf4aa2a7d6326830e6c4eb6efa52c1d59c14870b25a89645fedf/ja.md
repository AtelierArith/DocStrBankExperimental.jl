```
mediators(o::CausalTable; collapse_parents = true)
```

与えられた `CausalTable` オブジェクトから各治療-応答ペアの媒介変数を選択します。

# 引数

  * `o::CausalTable`: 各治療-応答ペアの媒介変数を抽出するための `CausalTable` オブジェクト。
  * `collape_parents::Bool`: オプションのパラメータで、治療-応答ペアが1つだけの場合や、すべてのペアが同じ媒介変数のセットを共有している場合に、出力を単一の `CausalTable` オブジェクトにまとめるかどうか。デフォルトは `true`。

# 戻り値

媒介変数のみを含む新しい `CausalTable`（応答が1つの場合、またはすべての応答が同じ媒介変数のセットを共有する場合）。そうでない場合は、各治療-応答ペアの媒介変数を含む CausalTable オブジェクトの行列で、行は応答を、列は治療を表します。
