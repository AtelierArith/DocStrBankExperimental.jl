`ClosenessCentrality(data::DataFrame)`

二部ネットワークの近接中心性を計算します。

# 引数

  * `data`: 二部ネットワークの隣接行列。

# 戻り値

  * `all`: すべての種の近接中心性。
  * `agroup`: 行の種の近接中心性。
  * `bgroup`: 列の種の近接中心性。

# 例

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(1);

print(data);

all,agroup,bgroup=ClosenessCentrality(data)
