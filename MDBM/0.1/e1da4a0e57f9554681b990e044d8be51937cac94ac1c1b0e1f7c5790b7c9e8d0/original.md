```
extract_paths(tree::PositionTree{N,T})
```

Extracts all root-to-leaf paths from a PositionTree.

# Arguments

  * `tree::PositionTree{N,T}`: The root of the PositionTree.

# Returns

  * An array of paths, each path being a vector of positions (as SVectors) from root to leaf.

# Example

```julia
root = PositionTree([1.0, 2.0, 3.0])
push!(root.subpoints, PositionTree([4.0, 5.0, 6.0]))
push!(root.subpoints, PositionTree([7.0, 8.0, 9.0]))

paths = extract_paths(root)
```
