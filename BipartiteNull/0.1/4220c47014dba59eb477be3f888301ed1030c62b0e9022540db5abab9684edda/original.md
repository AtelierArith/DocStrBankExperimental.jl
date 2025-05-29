`ModularityLabelPropagation(data::DataFrame)`

Calculate the modularity by label propagation.

# Argument

  * `data`:The adjacency matrix of a bipartite network.

# Return

  * `all`:Modularity of all species.
  * `agroup`:Modularity of the species of rows.
  * `bgroup`:Modularity of the species of columns.

# Example

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(1);

print(data);

all,agroup,bgroup=ModularityLabelPropagation(data)
