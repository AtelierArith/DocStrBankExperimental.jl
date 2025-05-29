```
Conv2D(filters, kernel_size, strides, activation, args...;kwargs...)
```

配置は (samples, rows, cols, channels) です (data*format='channels*last')

```julia
Conv2D(32, 3, 1, "relu")
```
