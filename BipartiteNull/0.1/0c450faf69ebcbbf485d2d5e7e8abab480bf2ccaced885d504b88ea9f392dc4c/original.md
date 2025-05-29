`MeanLocalClusteringCoefficient(data::DataFrame)`

Calculate the local cluster coefficient of the bipartite network.

# Argument

  * `data`:The adjacency matrix of a bipartite network.

# Return

  * `agroup`:Local cluster coefficient of the species of rows.
  * `bgroup`:Local cluster coefficient of the species of columns.

# Example

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(6);

print(data);

agroup,bgroup=MeanLocalClusteringCoefficient(data)
