```
are_in_same_leaf(x1::NTuple{d,Float64}, x2::NTuple{d,Float64}, tree::MondrianTree)
```

Check if two points are in the same leaf cell of a Mondrian tree.

# Examples

```jldoctest
d = 2
tree = MondrianTree(d, 0.0)
x1 = ntuple(i -> 0.2, d)
x2 = ntuple(i -> 0.7, d)
are_in_same_leaf(x1, x2, tree)

# output
true
```
