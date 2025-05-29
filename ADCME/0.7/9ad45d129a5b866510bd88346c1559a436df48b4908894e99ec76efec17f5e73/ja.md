```
Conv1D(filters, kernel_size, strides, activation, args...;kwargs...)
```

```julia
c = Conv1D(32, 3, 1, "relu")
x = rand(100, 6, 128) # 128の長さのベクトルが6つのタイムステップ（"チャンネル"）を持つ
y = c(x) # 形状=(100, 4, 32)
```
