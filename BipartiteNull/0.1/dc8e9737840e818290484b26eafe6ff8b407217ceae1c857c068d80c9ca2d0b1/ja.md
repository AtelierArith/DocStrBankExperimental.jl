`LabelPropagation(data::DataFrame)`

ラベル伝播によってラベルをマークします。

# 引数

  * `data`:二部ネットワークの隣接行列。
  * `maxiter`:収束が完了していない場合、maxiter回の反復後に返します。

# 戻り値

  * `newlabel`:頂点とラベルの情報。

# 例

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(1);

print(data);

newlabel=LabelPropagation(data)
