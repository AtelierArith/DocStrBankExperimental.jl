```
kernel_mean(ke::KernelEmbedding{Kernel,Measure}, samples::AbstractVector)
```

Compute the kernel mean of the kernel embedding `ke` for each one of  the `samples` $x_i$:

$$
    z_i = \int k(x, x_i)d\mu(x)
$$
