`LinksPerSpecies(data::DataFrame)`

Sum of links divided by number of species(consider the overall and individual situation).

# Argument

  * `data`:The adjacency matrix of a bipartite network.

# Return

  * `all`:Sum of links divided by number of all species.
  * `agroup`:Sum of links divided by number of the species of rows.
  * `bgroup`:Sum of links divided by number of the species of columns.

# Example

using BipartiteNull,DataFrames;

data=ExampleData(6);

print(data);

all,agroup,bgroup=LinksPerSpecies(data)
