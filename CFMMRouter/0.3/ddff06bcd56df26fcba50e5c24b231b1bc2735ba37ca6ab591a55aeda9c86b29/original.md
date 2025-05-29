```
GeometricMeanTwoCoin(R, w, γ, idx)
```

Creates a two coin geometric mean CFMM with coins `idx[1]` and `idx[2]`,  reserves `R`, fee `γ`, and weights `w` such that `w[1] + w[2] == 1.0`. Specifically, the invariant is

$$
\varphi(R) = R_1^{w_1}R_2^{w_2}.
$$
