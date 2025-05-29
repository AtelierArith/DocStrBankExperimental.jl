```
eachobs(data; kws...)
```

Return an iterator over `data`.

Supports the same arguments as [`DataLoader`](@ref). The `batchsize` default is `-1` here while it is `1` for `DataLoader`.

# Examples

```julia
X = rand(4,100)

for x in eachobs(X)
    # loop entered 100 times
    @assert typeof(x) <: Vector{Float64}
    @assert size(x) == (4,)
end

# mini-batch iterations
for x in eachobs(X, batchsize=10)
    # loop entered 10 times
    @assert typeof(x) <: Matrix{Float64}
    @assert size(x) == (4,10)
end

# support for tuples, named tuples, dicts
for (x, y) in eachobs((X, Y))
    # ...
end
```
