`Cscore(data::DataFrame)`

Calculate checkerboard units.

# Argument

  * `data`:The adjacency matrix of a bipartite network.

# Return

  * `all`:Checkerboard units/2*2 units.
  * `agroup`:C score of the species of rows.
  * `bgroup`:C score of the species of columns.

# Example

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(2);

print(data);

all,agroup,bgroup=Cscore(data)
