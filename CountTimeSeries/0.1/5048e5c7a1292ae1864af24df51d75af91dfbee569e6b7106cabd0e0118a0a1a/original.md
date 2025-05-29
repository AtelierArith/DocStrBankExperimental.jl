```
∘
```

Thinning operator for p∘X, d∘X or p∘d.

  * `p`: Thinning probability (∈ [0, 1])
  * `X`: Positive integer
  * `d`: Discrete distribution

Random numbers are generated according to (binomial) thinning.

`p∘X` computes $\sum_{i = 1}^X{Z_i}$ with $Z_i\sim\text{Bin}(1, p)$

`d∘X` computes $\sum_{i = 1}^X{Z_i}$ with $Z_i\sim$ `d`

`p∘d` computes $\sum_{i = 1}^X{Z_i}$ with $Z_i\sim\text{Bin}(1, n)$ and $X\sim$ `d`
