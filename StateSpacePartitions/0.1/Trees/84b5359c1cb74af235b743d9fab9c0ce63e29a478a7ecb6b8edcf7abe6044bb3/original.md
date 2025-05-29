```
Tree(; structured = false, arguments = (; minimum_probability = 0.01))
```

# Description

A tree is a data structure that can be used to store partitions of a state space.

# Keyword Arguments

  * `structured::Bool` - Whether the tree is structured or not.
  * `arguments::NamedTuple` - The arguments for the tree.

# Returns

  * `Tree` - Either a BinaryTree or an UnstructuredTree.
