`Null1(data::DataFrame)`

Nullモデル1、制約条件は種の数が変わらず、接続性が変わらないことです。

# 引数

  * `data`:二部ネットワークの隣接行列。

# 戻り値

  * `nulldata`:Nullモデル1によって生成されたデータフレーム。

# 例

using BipartiteNull,DataFrames;

data=ExampleData(7);

print(data);

nulldata=Null1(data)
