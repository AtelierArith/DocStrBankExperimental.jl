```
ones_like(o::Union{PyObject,Real, Array{<:Real}}, args...; kwargs...)
```

`o`と同じサイズのすべての要素が1のテンソルを返します。

# 例

```julia
a = rand(100,10)
b = ones_like(a)
@assert run(sess, b)≈ones(100,10)
```
