```
variation(x, m=mean(x); corrected=true)
```

Return the coefficient of variation of collection `x`, optionally specifying a precomputed mean `m`, and the optional correction parameter `corrected`. The coefficient of variation is the ratio of the standard deviation to the mean. If `corrected` is `false`, then `std` is calculated with denominator `n`. Else, the `std` is calculated with denominator `n-1`.
