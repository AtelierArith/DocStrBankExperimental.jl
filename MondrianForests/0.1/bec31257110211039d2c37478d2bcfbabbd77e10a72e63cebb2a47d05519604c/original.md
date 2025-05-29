```
get_center(tree::MondrianTree{d}) where {d}
```

Get the center point of the root cell of a Mondrian tree.

# Examples

```jldoctest
tree = MondrianTree(2, 3.0)
get_center(tree)

# output
(0.5, 0.5)
```
