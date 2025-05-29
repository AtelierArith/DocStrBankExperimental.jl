```
get_common_refinement(trees::Vector{MondrianTree{d}}) where {d}
```

Get the common refinement of several Mondrian trees, whose leaf cells are the intersections of all leaf cells in `trees`. Preserves the split times and returns a new equivalent `MondrianTree`.

# Examples

```julia
trees = [MondrianTree(2, 3.0) for _ in 1:3]
refined_tree = get_common_refinement(trees)
```
