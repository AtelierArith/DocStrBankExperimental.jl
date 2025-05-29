```
connectivity(model::AbstractModel)
```

Get the [nₑ × nₙ] sparse matrix where C[i, j] = -1 if element i starts at node j, and C[i,j] = 1 if element i ends at node j, and 0 otherwise.
