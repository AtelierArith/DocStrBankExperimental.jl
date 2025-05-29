```
FDPNSystem{FT, PNOrder}(state, Λ₁, Λ₂)
```

A `PNSystem` that contains information as variables from [`FastDifferentiation.jl`](https://docs.juliahub.com/General/FastDifferentiation/stable/).

See also [`fd_pnsystem`](@ref) for a particular instance of this type.  Note that this type also involves the type `FT`, which will be the float type of actual numbers that eventually get fed into (and will be passed out from) functions that use this system.  The correct type of `FDPNSystem` is used in calculating `𝓔′`.
