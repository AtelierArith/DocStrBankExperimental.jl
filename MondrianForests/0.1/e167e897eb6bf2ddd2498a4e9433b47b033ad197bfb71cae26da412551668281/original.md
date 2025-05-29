```
get_volume(tree::MondrianTree{d}) where {d}
```

Get the d-dimensional volume of the root cell of a Mondrian tree.

# Examples

```jldoctest
tree = MondrianTree(2, 3.0)
get_volume(tree)

# output
1.0
```
