```
combinations(a, n)
```

Generate all combinations of `n` elements from an indexable object `a`. Because the number of combinations can be very large, this function returns an iterator object. Use `collect(combinations(a, n))` to get an array of all combinations.
