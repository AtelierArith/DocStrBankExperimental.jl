```
cov_whitening!(C, regcoef)
```

In-place version of `cov_whitening(C, regcoef)`, in which the input matrix `C` will be overwritten during computation. This can be more efficient when `C` is no longer used.
