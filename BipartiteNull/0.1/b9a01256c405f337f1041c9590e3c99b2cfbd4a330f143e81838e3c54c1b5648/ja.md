`Bipartite2Graph(data::DataFrame,model::String)`

二部ネットワークの隣接行列を、射影または拡張を通じてGraphs.jlのネットワーク構造に変換します。

# 引数

  * `data`:二部ネットワークの隣接行列。
  * `fun`:変換方法を選択し、3つの関数をサポートします："Row2Edge","Col2Edge","Splicing4Matrix"。

# 戻り値

  * `omm`:射影または拡張による一位行列。
  * `graph`:Graphs.jlの下のネットワーク構造。

# 例

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(6);

print(data);

omm,graph=Bipartite2Graph(data,"Row2Edge")
