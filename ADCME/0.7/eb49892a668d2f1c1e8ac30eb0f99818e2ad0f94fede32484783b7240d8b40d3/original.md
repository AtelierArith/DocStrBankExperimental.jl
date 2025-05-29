```
zeros_like(o::Union{PyObject,Real, Array{<:Real}}, args...; kwargs...)
```

Returns a all-zero tensor, which has the same size as `o`.

# Example

```julia
a = rand(100,10)
b = zeros_like(a)
@assert run(sess, b)≈zeros(100,10)
```
