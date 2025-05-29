`Splicing4Matrix(data::DataFrame)`

The bipartite network is expanded into a one-mode network through matrix splicing.

# Argument

  * `data`:The adjacency matrix of a bipartite network.

# Return

  * `newdata`:One-mode network after splicing.

# Example

using BipartiteNull,DataFrames;

data=ExampleData(6);

print(data);

newdata=Splicing4Matrix(data)
