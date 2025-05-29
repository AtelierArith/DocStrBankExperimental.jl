```
difference(X::LazySet, Y::LazySet)
```

Compute the set difference of two sets.

### Input

  * `X` – set
  * `Y` – set

### Output

A set representing the difference $X ∖ Y$.

### Notes

The set difference is defined as:

$$
    X ∖ Y = \{x \mid x ∈ X \text{ and } x ∉ Y \}
$$
