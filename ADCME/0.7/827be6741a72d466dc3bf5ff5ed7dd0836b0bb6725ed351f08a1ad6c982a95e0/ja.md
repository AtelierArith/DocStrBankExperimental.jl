```
clip(o::Union{Array{Any}, Array{PyObject}}, vmin, vmax, args...;kwargs...)
```

`o`の値を範囲[`vmin`, `vmax`]にクリップします。

# 例

```julia
a = constant(3.0)
a = clip(a, 1.0, 2.0)
b = constant(rand(3))
b = clip(b, 0.5, 1.0)
```
