```
tsample!(B::AbstractArray, A::AbstractArray; [chunksize=5000])
```

Identical to `sample!` except that thread-based parallelism is used to accelerate the computation.

See also: [`sample!`](@ref), [`vsample!`](@ref), [`vtsample!`](@ref)
