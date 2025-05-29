```
eachobs(data, [obsdim])
```

Iterate over `data` one observation at a time. If supported by the type of `data`, a buffer will be preallocated and reused for memory efficiency.

IMPORTANT: Avoid using `collect`, because in general each iteration could return the same object with mutated values. If that behaviour is undesired use `obsview` instead.

```julia
X = rand(4,100)
for x in eachobs(X)
    # loop entered 100 times
    @assert typeof(x) <: Vector{Float64}
    @assert size(x) == (4,)
end
```

In the case of arrays it is assumed that the observations are represented by the last array dimension. This can be overwritten.

```julia
# This time flip the dimensions of the matrix
X = rand(100,4)
A = eachobs(X, obsdim=1)
# The behaviour remains the same as before
@assert eltype(A) <: Array{Float64,1}
@assert length(A) == 100
```

Multiple variables are supported (e.g. for labeled data)

```julia
for (x,y) in eachobs((X,Y))
    # ...
end
```

Note that internally `eachobs(data, obsdim)` maps to `BufferGetObs(obsview(data, obsdim))`.

```julia
@assert typeof(eachobs(X)) <: BufferGetObs
@assert typeof(eachobs(X).iter) <: ObsView
```

This means that the following code:

```julia
for obs in eachobs(data, obsdim)
    # ...
end
```

is roughly equivalent to:

```julia
obs = getobs(data, 1, obsdim) # use first element to preallocate buffer
for _ in obsview(data, obsdim)
    getobs!(obs, _) # reuse buffer each iteration
    # ...
end
```

see [`BufferGetObs`](@ref), [`obsview`](@ref), and [`getobs!`](@ref) for more info. also see [`eachbatch`](@ref) for a mini-batch version.
