`Null3(data::DataFrame)`

元のノードの次数分布を変更せずに保持します。

# 引数

  * `data`: 二部ネットワークの隣接行列。

# 戻り値

  * `nulldata`: nullモデル3によって生成されたデータフレーム。

# 例

using BipartiteNull,DataFrames;

data=ExampleData(7);

print(data);

nulldata=Null3(data)
