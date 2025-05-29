```
M = mappedarray(f, finv, A)
M = mappedarray(f, finv, A, B, C...)
```

creates a view of the array `A` that applies `f` to every element of `A`. The inverse function, `finv`, allows one to also set values of the view and, correspondingly, the values in `A`.

When multiple input arrays are supplied, `M[i] = f(A[i], B[i], C[i]...)`.
