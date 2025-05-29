```
placeholder(dtype::Type; kwargs...)
```

Creates a placeholder of the type `dtype`.

# Example

```julia
a = placeholder(Float64, shape=[20,10])
b = placeholder(Float64, shape=[]) # a scalar 
c = placeholder(Float64, shape=[nothing]) # a vector
```
