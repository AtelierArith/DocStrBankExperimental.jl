```
gram_operate(/, p::GramMatrix, α)
```

Computes the Gram matrix equal to `p / α`. On the opposite, `p / α` gives a polynomial equal to `p / α`. The polynomial `p / α` can also be obtained by `polynomial(gram_operate(/, p, α))`.
