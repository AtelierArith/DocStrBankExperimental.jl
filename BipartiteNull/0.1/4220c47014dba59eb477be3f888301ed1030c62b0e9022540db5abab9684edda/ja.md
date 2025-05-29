`ModularityLabelPropagation(data::DataFrame)`

ラベル伝播によるモジュラリティを計算します。

# 引数

  * `data`: 二部ネットワークの隣接行列。

# 戻り値

  * `all`: すべての種のモジュラリティ。
  * `agroup`: 行の種のモジュラリティ。
  * `bgroup`: 列の種のモジュラリティ。

# 例

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(1);

print(data);

all,agroup,bgroup=ModularityLabelPropagation(data)
