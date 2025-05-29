```
Conv3D(filters, kernel_size, strides, activation, args...;kwargs...)
```

The arrangement is (samples, rows, cols, channels) (data*format='channels*last')

```julia
c = Conv3D(32, 3, 1, "relu")
x = constant(rand(100, 10, 10, 10, 16))
y = c(x)
# shape=(100, 8, 8, 8, 32)
```
