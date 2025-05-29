```
result(problem) -> (x, y)
```

Return the best found point `(x, y)`.

Returns the point `(x, y)` from the dataset of the given problem such that `y` satisfies the constraints and `fitness(y)` is maximized. Returns nothing if the dataset is empty or if no feasible point is present.

Does not check whether `x` belongs to the domain as no exterior points should be present in the dataset.
