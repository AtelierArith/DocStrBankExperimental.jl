`BetweennessCentrality(data::DataFrame)`

Calculate the betweenness centrality of the bipartite network.

# Argument

  * `data`:The adjacency matrix of a bipartite network.

# Return

  * `all`:Betweenness centrality of all species.
  * `agroup`:Betweenness centrality of the species of rows.
  * `bgroup`:Betweenness centrality of the species of columns.

# Example

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(1);

print(data);

all,agroup,bgroup=BetweennessCentrality(data)
