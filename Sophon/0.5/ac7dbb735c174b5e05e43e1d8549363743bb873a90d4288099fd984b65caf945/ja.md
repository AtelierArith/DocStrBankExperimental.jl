```
Sine(in_dims::Int, out_dims::Int; omega::Real)
```

正弦層。

## 例

```julia
s = Sine(2, 2; omega=30.0f0) # 最初の層
s = Sine(2, 2) # 隠れ層
```
