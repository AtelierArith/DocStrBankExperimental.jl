```
ProductTwoCoin(R, γ, idx)
```

Creates a two coin product CFMM with coins `idx[1]` and `idx[2]`, reserves `R`, and fee `γ`. Specifically, the invariant is

$$
\varphi(R) = R_1R_2.
$$
