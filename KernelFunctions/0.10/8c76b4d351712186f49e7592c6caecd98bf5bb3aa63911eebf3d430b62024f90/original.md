```
nystrom(k::Kernel, X::AbstractMatrix, r::Real; obsdim)
```

If `obsdim=1`, equivalent to `nystrom(k, RowVecs(X), r)`. If `obsdim=2`, equivalent to `nystrom(k, ColVecs(X), r)`.

See also: [`ColVecs`](@ref), [`RowVecs`](@ref)
