```
is_in(x::NTuple{d,Float64}, tree::MondrianTree{d}) where {d}
```

Check if a point `x` is contained in the root cell of a Mondrian tree.

# Examples

```jldoctest
x = ntuple(i -> 0.2, 2)
tree = MondrianTree(2, 3.0)
is_in(x, tree)

# output
true
```
