```
tsample!(B::AbstractArray, A::AbstractArray; [chunksize=5000])
```

Identical to `sample!` except that thread-based parallelism is used to accelerate the computation. also, the underlying Marsaglia sampler uses `LoopVectorization`.

See also: [`vsample!`](@ref), [`sample!`](@ref), [`tsample!`](@ref)
