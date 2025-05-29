```
measure(a::AbstractVector{T}, X::AbstractVector{<:AbstractMonomial}; rtol=Base.rtoldefault(T), atol=zero(T))
```

各 `i` に対して `moment(a[i], X[i])` のモーメントを持つ測度を作成します。`X[i] == X[j]` である `i` と `j` が存在する場合、しかし `!isapprox(a[i], a[j]; rtol=rtol, atol=atol)` であるとエラーが発生します。
