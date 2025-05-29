```
euler_approx(ms::Vector{M}, args...) where {M<:ContinuousMachine}
euler_approx(ms::AbstractDict{S, M}, args...) where {S,M<:ContinuousMachine}
```

同一の `args` を持つ機械のコレクションに対して `euler_approx` を適用します。
