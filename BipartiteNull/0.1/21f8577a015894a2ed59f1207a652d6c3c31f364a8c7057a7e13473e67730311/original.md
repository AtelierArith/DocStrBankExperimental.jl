`Col2Edge(data::DataFrame)`

Convert nodes represented by columns to edges.

# Argument

  * `data`:The adjacency matrix of a bipartite network.

# Return

  * `newdata`:One-mode network after projection.

# Example

using BipartiteNull,DataFrames;

data=ExampleData(6);

print(data);

newdata=Col2Edge(data)
