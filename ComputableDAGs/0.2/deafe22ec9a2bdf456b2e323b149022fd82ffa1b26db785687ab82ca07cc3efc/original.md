GraphProperties

Representation of a [`DAG`](@ref)'s properties.

## Fields:

  * `data::Float64`: The total data transfer.
  * `compute_effort::Float64`: The total compute effort.
  * `compute_intensity::Float64`: The compute intensity, will always equal `compute_effort / data`.
  * `number_of_nodes::Int`: Number of [`Node`](@ref)s.
  * `number_of_edges::Int`: Number of [`Edge`](@ref)s.
