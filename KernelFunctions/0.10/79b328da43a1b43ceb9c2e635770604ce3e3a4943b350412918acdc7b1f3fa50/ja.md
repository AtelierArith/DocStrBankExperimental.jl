```
nystrom(k::Kernel, X::AbstractMatrix, S::AbstractVector{<:Integer}; obsdim)
```

`obsdim=1` の場合、`nystrom(k, RowVecs(X), S)` と同等です。`obsdim=2` の場合、`nystrom(k, ColVecs(X), S)` と同等です。

参照: [`ColVecs`](@ref), [`RowVecs`](@ref)
