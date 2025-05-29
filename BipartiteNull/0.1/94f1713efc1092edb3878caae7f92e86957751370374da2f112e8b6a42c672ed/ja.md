`Null2(data::DataFrame,coinpvalue::Float64)`

元のノードの次数分布を変更せずに保持します。

# 引数

  * `data`:二部ネットワークの隣接行列。
  * `coinpvalue`:真の出力の確率（0より大きく1未満）。小数点以下1桁または2桁の値を入力してください。

# 戻り値

  * `nulldata`: nullモデル2によって生成されたデータフレーム。

# 例

using BipartiteNull,DataFrames;

data=ExampleData(7);

print(data);

nulldata=Null2(data,0.5)
