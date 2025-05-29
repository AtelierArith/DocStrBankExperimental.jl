`ClosenessCentrality(data::DataFrame)`

Calculate the closeness centrality of the bipartite network.

# Argument

  * `data`:The adjacency matrix of a bipartite network.

# Return

  * `all`:Closeness centrality of all species.
  * `agroup`:Closeness centrality of the species of rows.
  * `bgroup`:Closeness centrality of the species of columns.

# Example

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(1);

print(data);

all,agroup,bgroup=ClosenessCentrality(data)
