```
vsum(A::DenseArray)
vsum(f, A::DenseArray)
```

Vectorized version of `sum`. Providing a function as the first argument will apply the function to each element of `A` before summing.
