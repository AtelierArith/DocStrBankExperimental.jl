```
euler_approx(rs::Vector{R}, args...) where {T,R<:ContinuousResourceSharer{T}}
euler_approx(rs::AbstractDict{S, R}, args...) where {S,T,R<:ContinuousResourceSharer{T}}
```

同一の `args` を持つリソースシェアラーのコレクションに対して `euler_approx` を適用します。
