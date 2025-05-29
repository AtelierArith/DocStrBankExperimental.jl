`RmZeroCol(data::DataFrame)`

すべての0列を削除します。

# 引数

  * `data`:二部ネットワークの隣接行列。

# 戻り値

  * `newdata`:データに基づいてすべてが0の列が削除されます。

# 例

using BipartiteNull,DataFrames;

data=ExampleData(1);

print(data);

newdata=RmZeroCol(data)
