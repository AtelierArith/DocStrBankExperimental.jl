```
M = mappedarray(f, A)
M = mappedarray(f, A, B, C...)
```

Create a view `M` of the array `A` that applies `f` to every element of `A`; `M == map(f, A)`, with the difference that no storage is allocated for `M`. The view is read-only (you can get values but not set them).

When multiple input arrays are supplied, `M[i] = f(A[i], B[i], C[i]...)`.
