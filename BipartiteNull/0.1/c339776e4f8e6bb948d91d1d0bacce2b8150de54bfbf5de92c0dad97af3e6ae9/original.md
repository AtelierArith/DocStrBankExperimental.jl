`Weight2Bool(data::DataFrame)`

Convert weight values in the matrix to Boolean values.

# Argument

  * `data`:Weight adjacency matrix of a bipartite network.

# Return

  * `newdata`:Boolean adjacency matrix of a bipartite network.

# Example

using BipartiteNull,DataFrames;

data=ExampleData(5);

print(data);

newdata=Weight2Bool(data)
