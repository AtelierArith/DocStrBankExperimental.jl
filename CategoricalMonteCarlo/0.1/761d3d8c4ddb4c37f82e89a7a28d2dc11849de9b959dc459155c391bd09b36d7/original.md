```
vsample!(B::AbstractArray, A::AbstractArray)
```

Identical to `sample!` except that except that the underlying Marsaglia sampler uses `LoopVectorization`.

See also: [`vtsample!`](@ref), [`sample!`](@ref), [`tsample!`](@ref)
