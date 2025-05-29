```
cov_whitening!(C)
```

In-place version of `cov_whitening(C)`, in which the input matrix `C` will be overwritten during computation. This can be more efficient when `C` is no longer used.
