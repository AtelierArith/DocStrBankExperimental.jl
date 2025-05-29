```
zeros_like(o::Union{PyObject,Real, Array{<:Real}}, args...; kwargs...)
```

`o`と同じサイズのすべてゼロのテンソルを返します。

# 例

```julia
a = rand(100,10)
b = zeros_like(a)
@assert run(sess, b)≈zeros(100,10)
```
