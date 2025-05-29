Nodal incidence matrix (Adjacency) is an N x N matrix describing a power system with N buses. It represents the directed connectivity of the buses in a power system.

The AdjacencyMatrix Struct is indexed using the Bus Numbers, no need for them to be sequential

# Arguments

  * `data::SparseArrays.SparseMatrixCSC{Int8, Int}`:       stores the incidence matrix
  * `axes<:NTuple{2, Dict}`:       Tuple containing two vectors, the first one contains the names of each       line of the network (each one related to a row of the Matrix in "data"),       the second one contains the names of each bus of the network (each one       related to a column of the Matrix in "data")
  * `lookup<:NTuple{2, Dict}`:       Tuple containing 2 Dictionaries mapping the number of rows and columns       with the names of branches and buses
  * `ref_bus_positions::Set{Int}`:       Vector containing the indexes of the columns of the BA matrix corresponding       to the reference buses
