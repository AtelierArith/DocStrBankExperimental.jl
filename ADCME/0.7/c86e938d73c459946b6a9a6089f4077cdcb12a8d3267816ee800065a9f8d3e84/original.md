```
ones_like(o::Union{PyObject,Real, Array{<:Real}}, args...; kwargs...)
```

Returns a all-one tensor, which has the same size as `o`.

# Example

```julia
a = rand(100,10)
b = ones_like(a)
@assert run(sess, b)≈ones(100,10)
```
