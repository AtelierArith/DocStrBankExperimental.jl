`Connectance(data::DataFrame)`

実現された可能なリンクの割合。

# 引数

  * `data`: 二部ネットワークの隣接行列。

# 戻り値

  * `value`: コネクタンス値。

# 例

using BipartiteNull,DataFrames;

data=ExampleData(6);

print(data);

value=Connectance(data)
