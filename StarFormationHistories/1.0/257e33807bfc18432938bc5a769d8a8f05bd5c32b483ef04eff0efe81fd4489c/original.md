```
LogarithmicAMR(constraint1, constraint2, T_max::Real=137//10,
               MH_func = MH_from_Z, dMH_dZ = dMH_dZ, Z_func = Z_from_MH,
               free::NTuple{2, Bool}=(true, true))
```

Construct an instance of `LogarithmicAMR` from MH constraints at two different lookback times. Each of `constraint1` and `constraint2` should be length-2 indexables (e.g., tuples) whose first element is a metallicity [M/H] and second element is a lookback time in Gyr. The order of the constraints does not matter.

# Examples

```jldoctest; setup = :(import StarFormationHistories: LogarithmicAMR)
julia> LogarithmicAMR((-2.5, 13.7), (-1.0, 0.0), 13.7) isa LogarithmicAMR{Float64}
true

julia> LogarithmicAMR((-2.5, 13.7), (-1.0, 0.0), 13.7) ==
           LogarithmicAMR((-1.0, 0.0), (-2.5, 13.7), 13.7)
true
```
