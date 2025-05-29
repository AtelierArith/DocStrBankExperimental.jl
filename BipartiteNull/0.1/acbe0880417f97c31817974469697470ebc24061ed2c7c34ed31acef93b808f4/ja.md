`Row2Edge(data::DataFrame)`

行で表されたノードをエッジに変換します。

# 引数

  * `data`:二部ネットワークの隣接行列。

# 戻り値

  * `newdata`:射影後の一部ネットワーク。

# 例

using BipartiteNull,DataFrames;

data=ExampleData(6);

print(data);

newdata=Row2Edge(data)
