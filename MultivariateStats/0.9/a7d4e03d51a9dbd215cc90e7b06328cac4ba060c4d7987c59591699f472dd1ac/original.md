```
predict(M::KernelPCA, x)
```

Transform out-of-sample transformation of `x` into a kernel space of the model `M`.

Here, `x` can be either a vector of length `d` or a matrix where each column is an observation.
