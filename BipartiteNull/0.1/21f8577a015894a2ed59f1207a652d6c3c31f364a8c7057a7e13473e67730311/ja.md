`Col2Edge(data::DataFrame)`

列で表されたノードをエッジに変換します。

# 引数

  * `data`: 二部ネットワークの隣接行列。

# 戻り値

  * `newdata`: 投影後の一部ネットワーク。

# 例

using BipartiteNull,DataFrames;

data=ExampleData(6);

print(data);

newdata=Col2Edge(data)
