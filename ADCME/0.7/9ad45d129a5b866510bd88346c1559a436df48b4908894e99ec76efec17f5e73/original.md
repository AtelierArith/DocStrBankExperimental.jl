```
Conv1D(filters, kernel_size, strides, activation, args...;kwargs...)
```

```julia
c = Conv1D(32, 3, 1, "relu")
x = rand(100, 6, 128) # 128-length vectors with 6 timesteps ("channels")
y = c(x) # shape=(100, 4, 32)
```
