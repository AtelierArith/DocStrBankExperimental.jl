```
vlogsumexp(A::AbstractArray)
```

Compute the log of the sum of exponentials of each element of `A`. Care is taken to ensure that the computation will not overflow/underflow, but the caller should be aware that `+Inf` and `NaN` are not handled.
