```
euler_approx(ms::Vector{M}, args...) where {M<:ContinuousMachine}
euler_approx(ms::AbstractDict{S, M}, args...) where {S,M<:ContinuousMachine}
```

Map `euler_approx` over a collection of machines with identical `args`.
