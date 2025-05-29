`NetworkLevel(data::DataFrame,ID::String)`

Integration of some indicators of the bipartite network.

# Argument

  * `data`:The adjacency matrix of a bipartite network.
  * `ID`:The name of the network.

# Return

  * `df`:Integration of some indicators of the bipartite network.

# Example

using BipartiteNull,DataFrames;

data=ExampleData(7);

print(data);

df=NetworkLevel(data,"original")
