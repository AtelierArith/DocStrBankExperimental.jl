```
get_leaf_containing(x::NTuple{d,Float64}, tree::MondrianTree{d}) where {d}
```

Get the leaf of a Mondrian tree containing a point `x`.

# Examples

```julia
d = 2
x = ntuple(i -> 0.2, d)
tree = MondrianTree(d, 3.0)
get_leaf_containing(x, tree)
```
