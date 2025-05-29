```
kernel_mean(ke::KernelEmbedding{Kernel,Measure}, samples::AbstractVector)
```

カーネル埋め込み `ke` のカーネル平均を各 `samples` $x_i$ に対して計算します：

$$
    z_i = \int k(x, x_i)d\mu(x)
$$
