`Connectance(data::DataFrame)`

Realised proportion of possible links.

# Argument

  * `data`:The adjacency matrix of a bipartite network.

# Return

  * `value`:Connectance value.

# Example

using BipartiteNull,DataFrames;

data=ExampleData(6);

print(data);

value=Connectance(data)
