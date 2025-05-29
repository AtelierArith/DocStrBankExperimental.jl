```
front(v)
front(f, v; atol1=0, atol2=0)
```

Construct a Pareto front of `v`. Elements of `v` will be masked by `f` in the computation.

The first and second (objective) coordinates have to differ by at least `atol1`, `atol2`, respectively, relatively to the latest point on the front.

# Examples

```jldocstest
v = [(1,2), (2,3), (2,1)]
front(v)

# output
[(1, 2), (2, 1)]
```

```jldoctest
v = [(1, (1, 2)), (2, (2, 3)), (3, (2, 1))]
front(x -> x[2], v)

# output

[(1, (1, 2)), (3, (2, 1))]
```

```jldoctest
v = [(1, 2), (2, 1.99), (3, 1)]
front(v; atol2 = 0.2)

# output

[(1, 2), (3, 1)]
```
