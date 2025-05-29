```julia
DeriDistFunction(E ; T::Float64, mu::Float64=0.0, stat::Int64=-1)
```

derivative of [`dist`](@ref) w.r.t the energy. `stat`=1 –> Bose-Einstein distribution, and `stat`=-1 –> Fermi distribution.
