`GlobalClusterCoefficient(data::DataFrame)`

Calculate the global cluster coefficient of the bipartite network.

# Argument

  * `data`:The adjacency matrix of a bipartite network.

# Return

  * `agroup`:Global cluster coefficient of the species of rows.
  * `bgroup`:Global cluster coefficient of the species of columns.

# Example

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(6);

print(data);

agroup,bgroup=GlobalClusterCoefficient(data)
