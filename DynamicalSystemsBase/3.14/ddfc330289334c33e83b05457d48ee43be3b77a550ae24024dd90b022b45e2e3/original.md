```
StroboscopicMap <: DiscreteTimeDynamicalSystem
StroboscopicMap(ds::CoupledODEs, period::Real) → smap
StroboscopicMap(period::Real, f, u0, p = nothing; kwargs...)
```

A discrete time dynamical system that produces iterations of a time-dependent (non-autonomous) [`CoupledODEs`](@ref) system exactly over a given `period`. The second signature first creates a [`CoupledODEs`](@ref) and then calls the first.

`StroboscopicMap` follows the [`DynamicalSystem`](@ref) interface. In addition, the function `set_period!(smap, period)` is provided, that sets the period of the system to a new value (as if it was a parameter). As this system is in discrete time, [`current_time`](@ref) and [`initial_time`](@ref) are integers. The initial time is always 0, because `current_time` counts elapsed periods. Call these functions on the `parent` of `StroboscopicMap` to obtain the corresponding continuous time. In contrast, [`reinit!`](@ref) expects `t0` in continuous time.

The convenience constructor

```julia
StroboscopicMap(T::Real, f, u0, p = nothing; diffeq, t0 = 0) → smap
```

is also provided.

See also [`PoincareMap`](@ref).
