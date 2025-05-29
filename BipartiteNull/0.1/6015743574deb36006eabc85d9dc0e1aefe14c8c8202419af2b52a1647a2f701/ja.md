`Splicing4Matrix(data::DataFrame)`

二部ネットワークは、行列スプライシングを通じて一元ネットワークに拡張されます。

# 引数

  * `data`: 二部ネットワークの隣接行列。

# 戻り値

  * `newdata`: スプライシング後の一元ネットワーク。

# 例

using BipartiteNull,DataFrames;

data=ExampleData(6);

print(data);

newdata=Splicing4Matrix(data)
