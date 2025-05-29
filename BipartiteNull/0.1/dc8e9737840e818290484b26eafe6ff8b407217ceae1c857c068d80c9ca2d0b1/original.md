`LabelPropagation(data::DataFrame)`

Mark the label by label propagation.

# Argument

  * `data`:The adjacency matrix of a bipartite network.
  * `maxiter`:Return after maxiter iterations if convergence has not completed.

# Return

  * `newlabel`:Vertex and label information.

# Example

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(1);

print(data);

newlabel=LabelPropagation(data)
