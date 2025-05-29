`RmZeroCol(data::DataFrame)`

Delete all 0 columns.

# Argument

  * `data`:Adjacency matrix of a bipartite network.

# Return

  * `newdata`:The columns that are all 0 are deleted on the basis of data.

# Example

using BipartiteNull,DataFrames;

data=ExampleData(1);

print(data);

newdata=RmZeroCol(data)
