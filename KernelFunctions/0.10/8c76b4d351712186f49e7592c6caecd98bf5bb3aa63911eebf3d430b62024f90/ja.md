```
nystrom(k::Kernel, X::AbstractMatrix, r::Real; obsdim)
```

`obsdim=1` の場合、`nystrom(k, RowVecs(X), r)` と同等です。`obsdim=2` の場合、`nystrom(k, ColVecs(X), r)` と同等です。

参照: [`ColVecs`](@ref), [`RowVecs`](@ref)
