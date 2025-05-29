`GlobalClusterCoefficientQuaternion(data::DataFrame)`

二部ネットワークのグローバルクラスタ係数（クォータニオン）を計算します。

# 引数

  * `data`: 二部ネットワークの隣接行列。

# 戻り値

  * `value`: グローバルクラスタ係数（クォータニオン）。

# 例

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(3);

print(data);

vlaue=GlobalClusterCoefficientQuaternion(data)
