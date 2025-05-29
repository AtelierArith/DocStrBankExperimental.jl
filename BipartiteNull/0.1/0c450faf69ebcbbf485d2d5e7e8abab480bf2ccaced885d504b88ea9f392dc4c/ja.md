`MeanLocalClusteringCoefficient(data::DataFrame)`

二部ネットワークの局所クラスタ係数を計算します。

# 引数

  * `data`: 二部ネットワークの隣接行列。

# 戻り値

  * `agroup`: 行の種の局所クラスタ係数。
  * `bgroup`: 列の種の局所クラスタ係数。

# 例

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(6);

print(data);

agroup,bgroup=MeanLocalClusteringCoefficient(data)
