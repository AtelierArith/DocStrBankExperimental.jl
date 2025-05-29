```
Multinomial(vec)
```

returns the multinomial coefficient whose top index is the sum of `vec` (an array of `Int`s) and whose bottom indices are given by `vec`.

This may also be called with a common-separated list of arguments, that is, either of `Multinomial([1,2,3])` or `Multinomial(1,2,3)`. The result is `60` in both cases as these equal `6!/(1! 2! 3!)`.

**Warning**: This is not the same as `MultiChoose`.
