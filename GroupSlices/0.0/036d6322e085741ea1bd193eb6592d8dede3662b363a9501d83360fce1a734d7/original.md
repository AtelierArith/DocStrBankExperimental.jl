```
groupslices(V::AbstractVector)
```

Returns a vector of integers the same length as `V`, which in place of each entry `x` has the index of the first entry of `V` which is equal to `x`. This is true:

```
all(x == V[i] for (x,i) in zip(V, groupslices(V)))
```
