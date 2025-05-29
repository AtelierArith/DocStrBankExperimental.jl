`DegreeCentrality(data::DataFrame)`

Calculate the degree centrality of the bipartite network.

# Argument

  * `data`:The adjacency matrix of a bipartite network.

# Return

  * `all`:Degree centrality of all species.
  * `agroup`:Degree centrality of the species of rows.
  * `bgroup`:Degree centrality of the species of columns.

# Example

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(1);

print(data);

all,agroup,bgroup=DegreeCentrality(data)
