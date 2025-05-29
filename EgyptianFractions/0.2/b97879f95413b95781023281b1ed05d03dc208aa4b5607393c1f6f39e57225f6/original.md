Performs a harmonic expansion of the given rational number into a sum of fractions of the form `1/2 + 1/3 + ...`, and concludes the remainder of the expansion using `efgreedy` if the given rational number cannot be represented as a sum in the harmonic sequence.

If the second argument is specified, the expansion will begin using that value as the first denominator.  In other words, while `efharmonic(r)` will return an array beginning `[2, 3, ...]`, `efharmonic(r, 3)` will return an array beginning `[3, 4, ...]`, and so on.

This function will throw an exception if the second argument `f ≤ 1`.

This function returns only the denominators of the expansion (i.e., only `[a_1, a_2, ...]`).  If the given rational number `r` satisfies `r ≥ 1`, the first `n` elements of the expansion will be 1, where `n = floor(r)`.  If the given rational number `r` satisfies `r < 0`, all returned denominators will be less than 0, so that the relationship

```
r == sum(1 .// efharmonic(r))
```

is always true.
