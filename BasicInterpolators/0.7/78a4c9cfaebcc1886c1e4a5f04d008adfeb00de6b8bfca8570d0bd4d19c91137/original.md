```
findcell(q, V, n)
```

Use bisection search to find the cell containing `q`, assuming `V` is a sorted vector of `n` coordinates. The returned integer is the index of the element in `V` immediately less than `q`. For example, if `findcell` returns 2, then `q ∈ [V[2],V[3])`. If `q` is less than every element in `V`, 1 is returned, indicating the first cell in `V`. If `q` is greater than every element in `V`, `length(V)-1` is returned, indicating the last cell in `V`.
