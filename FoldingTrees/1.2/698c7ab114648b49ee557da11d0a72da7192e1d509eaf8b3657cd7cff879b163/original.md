```
itr = nodes(node)
```

Create an iterator `itr` that will return the nodes, rather than the node data.

# Example

```julia
julia> foreach(unfold!, nodes(root))
```

would ensure that each node in the tree is unfolded.
