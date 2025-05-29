# Create a kernel for the inversion of 1D data.

```
create_kernel(seq, x, X)
```

  * `seq` is the pulse sequence (e.g. IR, CPMG, PFG)
  * `x` is the experiment x axis (time or b factor etc.)
  * `X` is the range for the output x axis (T1, T2, D etc.)

The output is a matrix, `K`.
