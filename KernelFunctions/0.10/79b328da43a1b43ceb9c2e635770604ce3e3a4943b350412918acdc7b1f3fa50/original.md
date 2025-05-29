```
nystrom(k::Kernel, X::AbstractMatrix, S::AbstractVector{<:Integer}; obsdim)
```

If `obsdim=1`, equivalent to `nystrom(k, RowVecs(X), S)`. If `obsdim=2`, equivalent to `nystrom(k, ColVecs(X), S)`.

See also: [`ColVecs`](@ref), [`RowVecs`](@ref)
