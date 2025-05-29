`Cscore22(data::DataFrame)`

チェッカーボードユニットを計算します。

# 引数

  * `data`: 二部ネットワークの隣接行列。

# 戻り値

  * `all`: チェッカーボードユニット/2*2ユニット。
  * `agroup`: 行の種のCスコア。
  * `bgroup`: 列の種のCスコア。

# 例

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(2);

print(data);

all,agroup,bgroup=Cscore22(data)
