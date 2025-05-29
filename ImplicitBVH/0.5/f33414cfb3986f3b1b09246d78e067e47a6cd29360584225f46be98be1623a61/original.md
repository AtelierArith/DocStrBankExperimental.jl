```julia
struct ImplicitTree{T<:Integer}
```

Implicit binary tree for `num_leaves` elements, where nodes are labelled according to a breadth-first search.

# Methods

```
ImplicitTree(num_leaves::Integer)
ImplicitTree{T}(num_leaves::Integer)
```

# Fields

  * `levels::Integer`: Number of levels in the tree.
  * `real_leaves::Integer`: Number of real leaves - i.e. the elements from which the tree was constructed.
  * `real_nodes::Integer`: Total number of real nodes in tree.
  * `virtual_leaves::Integer`: Number of virtual leaves needed at the bottom level to have a perfect binary tree.
  * `virtual_nodes::Integer`: Total number of virtual nodes in tree needed for a complete binary tree.

# Examples

```julia
julia> using ImplicitBVH

# Given 5 geometric elements (e.g. bounding boxes) we construct the following implicit tree
# having the 5 real leaves at implicit indices 8-12 plus 3 virtual leaves.
#         Nodes & Leaves                Tree Level
#               1                       1
#       2               3               2
#   4       5       6        7v         3
# 8   9   10 11   12 13v  14v  15v      4
julia> tree = ImplicitTree(5)
ImplicitTree{Int64}
  levels: Int64 4
  real_leaves: Int64 5
  real_nodes: Int64 11
  virtual_leaves: Int64 3
  virtual_nodes: Int64 4

# We can keep all tree nodes in a contiguous vector with no extra padding for the virtual
# nodes by computing the real memory index of real nodes; e.g. real memory index of node 8
# skips node 7 which is virtual:
julia> memory_index(tree, 8)
7

# We can get the range of indices of real nodes on a given level
julia> level_indices(tree, 3)
(4, 6)

# And we can check if a node at a given implicit index is virtual
julia> isvirtual(tree, 6)
false

julia> isvirtual(tree, 7)
true
```
