`Weight2Bool(data::DataFrame)`

重みの値をブール値に変換します。

# 引数

  * `data`: 二部ネットワークの重み隣接行列。

# 戻り値

  * `newdata`: 二部ネットワークのブール隣接行列。

# 例

using BipartiteNull,DataFrames;

data=ExampleData(5);

print(data);

newdata=Weight2Bool(data)
