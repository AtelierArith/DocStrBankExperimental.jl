`Bipartite2Graph(data::DataFrame,model::String)`

Convert the adjacency matrix of the bipartite network into the network structure under Graphs.jl through projection or expansion.

# Argument

  * `data`:The adjacency matrix of a bipartite network.
  * `fun`:Select the conversion method and support three functions:"Row2Edge","Col2Edge","Splicing4Matrix".

# Return

  * `omm`:One-mode matrix by projection or expansion.
  * `graph`:The network structure under Graphs.jl.

# Example

using BipartiteNull,DataFrames,Graphs;

data=ExampleData(6);

print(data);

omm,graph=Bipartite2Graph(data,"Row2Edge")
