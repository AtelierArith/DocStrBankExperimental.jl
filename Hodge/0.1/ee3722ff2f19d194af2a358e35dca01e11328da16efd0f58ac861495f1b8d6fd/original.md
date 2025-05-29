```
numsimplices(sc[, k])
```

Return the number of k-dimensional simplices of `sc`.

If the parameter `k` is not given, return the total number of simplices including the empty face.

This function is a more efficient implementation of `length ∘ simplices`.
