```
getparentindex(idx, tree_type)
```

Get the parent index of the child node `idx`.

# Arguments

  * `idx::T where T<:Integer`: Index of child node.
  * `tree_type::Symbol`: Tree type, ie. `:binary` tree or `:quad` tree.

# Returns

  * `::T`: Index of parent node.
