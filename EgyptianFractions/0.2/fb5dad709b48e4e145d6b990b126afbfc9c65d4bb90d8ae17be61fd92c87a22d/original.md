Performs a greedy (Fibonacci–Sylvester) expansion of the given rational number into a sum of fractions of the form `1/a_1 + 1/a_2 + ...`, but only using odd denominators.

It can be shown that, for any rational number `x/y` where `y` is odd, you can write this as a finite sum of fractions where all denominators are odd.  This method sometimes produces an expansion with fewer elements than the traditional greedy algorithm.

This function will throw an exception if the denominator of the rational number supplied is even.

This function returns only the denominators of the expansion (i.e., only `[a_1, a_2, ...]`).  If the given rational number `r` satisfies `r ≥ 1`, the first `n` elements of the expansion will be 1, where `n = floor(r)`.  If the given rational number `r` satisfies `r < 0`, all returned denominators will be less than 0, so that the relationship

```
r == sum(1 .// efoddgreedy(r))
```

is always true.
