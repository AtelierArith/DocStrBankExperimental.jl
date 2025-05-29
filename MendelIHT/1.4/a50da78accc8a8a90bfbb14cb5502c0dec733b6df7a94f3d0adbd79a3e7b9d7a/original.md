```
score!(v::IHTVariable{T})
```

Calculates the score (gradient) `X^T * W * (y - g(x^T b))` for different GLMs.  W is a diagonal matrix where `w[i, i] = dμ/dη / var(μ)` (see documentation)
