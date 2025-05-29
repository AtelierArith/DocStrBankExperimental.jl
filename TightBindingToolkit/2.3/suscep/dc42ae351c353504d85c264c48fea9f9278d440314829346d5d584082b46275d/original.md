```julia
FillChis!(chi::Susceptibility; fill_BZ::Bool=false, a::Int64=3, b::Int64=3)
```

function to calculate susceptibility at a all given Ω=`Omegas`, but for all `Q` present in the given path, and along a fixed direction given by `a` and `b`.
