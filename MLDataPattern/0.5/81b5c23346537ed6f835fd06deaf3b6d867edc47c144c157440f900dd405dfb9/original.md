```
eachbatch(data, [size], [count], [obsdim])
```

Iterate over `data` one batch at a time. If supported by the type of `data`, a buffer will be preallocated and reused for memory efficiency.

IMPORTANT: Avoid using `collect`, because in general each iteration could return the same object with mutated values. If that behaviour is undesired use `BatchView` instead.

The (constant) batch-size can be either provided directly using `size` or indirectly using `count`, which derives `size` based on `nobs`. In the case that the size of the dataset is not dividable by the specified (or inferred) `size`, the remaining observations will be ignored.

```julia
X = rand(4,150)
for x in eachbatch(X, size = 10) # or: eachbatch(X, count = 15)
    # loop entered 15 times
    @assert typeof(x) <: Matrix{Float64}
    @assert size(x) == (4,10)
end
```

In the case of arrays it is assumed that the observations are represented by the last array dimension. This can be overwritten.

```julia
# This time flip the dimensions of the matrix
X = rand(150,4)
A = eachbatch(X, size = 10, obsdim = 1)
# The behaviour remains the same as before
@assert eltype(A) <: Array{Float64,2}
@assert length(A) == 15
```

Multiple variables are supported (e.g. for labeled data)

```julia
for (x,y) in eachbatch((X,Y))
    # ...
end
```

Note that internally `eachbatch(data, ...)` maps to `BufferGetObs(batchview(data, ...))`.

```julia
@assert typeof(eachbatch(X)) <: BufferGetObs
@assert typeof(eachbatch(X).iter) <: BatchView
```

This means that the following code:

```julia
for batch in eachbatch(data, batchsize, obsdim)
    # ...
end
```

is roughly equivalent to:

```julia
batch = getobs(data, collect(1:batchsize), obsdim) # use first element to preallocate buffer
for _ in batchview(data, batchsize, obsdim)
    getobs!(batch, _) # reuse buffer each iteration
    # ...
end
```

see [`BufferGetObs`](@ref), [`batchview`](@ref), and [`getobs!`](@ref) for more info. also see [`eachobs`](@ref) for a single-observation version.
