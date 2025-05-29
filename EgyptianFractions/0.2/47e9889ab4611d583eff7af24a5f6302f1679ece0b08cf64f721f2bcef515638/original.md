Performs a greedy (Fibonacci–Sylvester) expansion of the given rational number into a sum of fractions of the form `1/a_1 + 1/a_2 + ...`

This function returns only the denominators of the expansion (i.e., only `[a_1, a_2, ...]`).  If the given rational number `r` satisfies `r ≥ 1`, the first `n` elements of the expansion will be 1, where `n = floor(r)`.  If the given rational number `r` satisfies `r < 0`, all returned denominators will be less than 0, so that the relationship

```
r == sum(1 .// efgreedy(r))
```

is always true.
