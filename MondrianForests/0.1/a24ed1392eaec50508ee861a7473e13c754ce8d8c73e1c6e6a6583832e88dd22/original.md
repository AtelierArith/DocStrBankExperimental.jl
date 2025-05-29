```
restrict(tree::MondrianTree{d}, time::Float64) where {d}
```

Restrict a Mondrian tree to a stopping time.

# Examples

```julia
tree = MondrianTree(2, 3.0)
restrict(tree, 2.0)
```
