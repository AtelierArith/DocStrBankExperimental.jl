```
fixnode!(node::AbstractNode, fixity::Symbol)
```

Fix the DOFs of a node to a common boundary condition.

# Arguments

  * `node::AbstractNode`node to modify
  * `fixity::Symbol` boundary condition to apply. Available boundary conditions:

      * :free
      * :fixed
      * :pinned
      * :(x/y/z)free
      * :(x/y/z)fixed
