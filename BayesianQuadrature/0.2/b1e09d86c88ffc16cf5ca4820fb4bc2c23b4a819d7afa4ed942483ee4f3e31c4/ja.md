```
kernel_variance(ke::KernelEmbedding{Kernel,Measure})
```

与えられたカーネル埋め込みのカーネル分散を計算します：

$$
    C = \int\int k(x,x')d\mu(x)d\mu(x')
$$
