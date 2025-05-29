```
Conv2D(filters, kernel_size, strides, activation, args...;kwargs...)
```

The arrangement is (samples, rows, cols, channels) (data*format='channels*last')

```julia
Conv2D(32, 3, 1, "relu")
```
