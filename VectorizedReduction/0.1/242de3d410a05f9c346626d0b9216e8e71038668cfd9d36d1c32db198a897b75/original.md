```
vargmin(f, A::AbstractArray, dims=:)
```

Return the index of the argument which minimizes `f` over the dimensions `dims`, which may be `::Int`, `::NTuple{M, Int} where {M}` or `::Colon`. Expands upon the functionality provided in Julia Base.

# Additional Notes

Due to the current limitations of LoopVectorization, searches over the first dimension of an array are not well-supported. A workaround is possible by reshaping `A` but the resultant performance is often only on par with `argmin`. As a temporary convenience, `vargmin1` is provided for explicit uses of the re-shaping strategy, though the user is cautioned as to the performance problems.
