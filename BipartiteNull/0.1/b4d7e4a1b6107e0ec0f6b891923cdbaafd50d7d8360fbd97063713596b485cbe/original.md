`RmZeroRow(data::DataFrame)`

Delete all 0 rows.

# Argument

  * `data`:Adjacency matrix of a bipartite network.

# Return

  * `newdata`:The rows that are all 0 are deleted on the basis of data.

# Example

using BipartiteNull,DataFrames;

data=ExampleData(1);

print(data);

newdata=RmZeroRow(data)
