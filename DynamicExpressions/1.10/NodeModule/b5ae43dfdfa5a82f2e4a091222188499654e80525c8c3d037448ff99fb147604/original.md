```
AbstractNode
```

Abstract type for binary trees. Must have the following fields:

  * `degree::Integer`: Degree of the node. Either 0, 1, or 2. If 1,   then `l` needs to be defined as the left child. If 2,   then `r` also needs to be defined as the right child.
  * `l::AbstractNode`: Left child of the current node. Should only be   defined if `degree >= 1`; otherwise, leave it undefined (see the   the constructors of [`Node{T}`](@ref) for an example).   Don't use `nothing` to represent an undefined value   as it will incur a large performance penalty.
  * `r::AbstractNode`: Right child of the current node. Should only   be defined if `degree == 2`.
