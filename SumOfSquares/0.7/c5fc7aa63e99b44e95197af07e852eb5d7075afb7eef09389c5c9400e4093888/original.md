```
gram_operate(::typeof(+), p::GramMatrix, q::GramMatrix)
```

Computes the Gram matrix equal to the sum between `p` and `q`. On the opposite, `p + q` gives a polynomial equal to `p + q`. The polynomial `p + q` can also be obtained by `polynomial(gram_operate(+, p, q))`.
