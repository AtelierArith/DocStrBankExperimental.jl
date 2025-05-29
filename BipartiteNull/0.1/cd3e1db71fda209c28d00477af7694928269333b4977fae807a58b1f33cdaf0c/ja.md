`NetworkLevel(data::DataFrame,ID::String)`

二部ネットワークのいくつかの指標の統合。

# 引数

  * `data`:二部ネットワークの隣接行列。
  * `ID`:ネットワークの名前。

# 戻り値

  * `df`:二部ネットワークのいくつかの指標の統合。

# 例

using BipartiteNull,DataFrames;

data=ExampleData(7);

print(data);

df=NetworkLevel(data,"original")
