`GlobalClusterCoefficientQuaternion(data::DataFrame)`

Calculate the global cluster coefficient(quaternion) of the bipartite network.

# Argument

  * `data`:The adjacency matrix of a bipartite network.

# Return

  * `value`:Global cluster coefficient(quaternion).

# Example

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(3);

print(data);

vlaue=GlobalClusterCoefficientQuaternion(data)
