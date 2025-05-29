```
MondrianTree(id::String, lambda::Float64, lower::NTuple{d,Float64},
             upper::NTuple{d,Float64}, creation_time::Float64) where {d}
```

Sample a Mondrian tree with a given id, lifetime, lower and upper cell coordinates, and creation time. To be used in internal construction methods.

# Examples

```julia
id = ""
lambda = 3.0
lower = ntuple(i -> 0.2, d)
upper = ntuple(i -> 0.7, d)
creation_time = 0.0
tree = MondrianTree(id, lambda, lower, upper, creation_time)
```
