```julia
struct NodeBB
```

Store information associated with each node in the branch-and-bound tree.

  * `lower_variable_bounds::Vector{Float64}`: Lower bounds of variable box.
  * `upper_variable_bounds::Vector{Float64}`: Upper bounds of variable box.
  * `is_integer::BitVector`: Is dimension integer valued
  * `continuous::Bool`: Are all dimensions continuous (or fixed)
  * `lower_bound::Float64`: Lower bound of problem solution on nodeBB
  * `upper_bound::Float64`: Upper bound of problem solution on nodeBB
  * `depth::Int64`: Depth of node in B&B tree.
  * `cont_depth::Int64`: Depth of first parent in B&B tree that was continuously valued
  * `id::Int64`: Unique ID for each node.
  * `branch_direction::EAGO.BranchDirection`: Whether last branch was negative or positive in direction
  * `last_branch::Int64`: Dimension of last branch
  * `branch_extent::Float64`: Extent of last branch (using for psuedocost calculation)
