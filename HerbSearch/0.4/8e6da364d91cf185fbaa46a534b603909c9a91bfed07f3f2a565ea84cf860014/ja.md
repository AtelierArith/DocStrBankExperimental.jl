```
VLSNSearchIterator(spec, cost_function, enumeration_depth = 2, evaluation_function::Function=HerbInterpret.execute_on_input) = StochasticSearchIterator(
```

Very Large Scale Neighbourhood Searchアルゴリズムに従って実行されるイテレータを返します。

  * `spec` : 例の配列
  * `cost_function` : 提案されたプログラムを評価するコスト関数
  * `vlsn_neighbourhood_depth` : 一度に最良のプログラムを検索するための列挙深度
  * `evaluation_function` : 生成されたプログラムを評価し、出力を生成する評価関数

提案関数は、与えられた`enumeration_depth`のすべての可能なプログラムで構成されています。受け入れ関数は、`cost_function`に従って最も低いコストのプログラムを受け入れます。アルゴリズムの温度値は時間とともに一定のままです。
