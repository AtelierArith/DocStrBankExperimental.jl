`NullNetworkLevel(data::DataFrame;num=100,fun="Null3",coinpvalue=0.5)`

二部ネットワーク（元のモデルとヌルモデル）のいくつかの指標の統合。

# 引数

  * `data`:二部ネットワークの隣接行列。
  * `num`:生成されるヌルモデルの数量。
  * `fun`:ヌルモデルの生成方法。 "Null1"、"Null2"、"Null3"のいずれかを選択できます。
  * `coinpvalue`:真の出力の確率（0より大きく1未満）。小数点以下1桁または2桁の値を入力してください。

# 戻り値

  * `df`:二部ネットワーク（元のモデルとヌルモデル）のいくつかの指標の統合。

# 例

using BipartiteNull,DataFrames;

data=ExampleData(2);

print(data);

df=NullNetworkLevel(data)
