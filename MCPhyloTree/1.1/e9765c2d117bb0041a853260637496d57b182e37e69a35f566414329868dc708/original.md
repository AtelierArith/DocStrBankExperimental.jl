```
find_num(root::T, num::Int64, rn::Vector{T})::Bool  where T<:AbstractNode
```

Do a post order traversal to find the node corresponding to the `num`.

Returns true if node is found, false otherwise. Desired Node is pushed to rn.

  * `root` : root Node of tree to be searched.
  * `num` : number of desired Node.
  * `rn` : Vector of Nodes; desired Node is pushed to this vector when found.
