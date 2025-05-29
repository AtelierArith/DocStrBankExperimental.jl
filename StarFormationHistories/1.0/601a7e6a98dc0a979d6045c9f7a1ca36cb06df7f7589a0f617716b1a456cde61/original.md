```
LinearAMR(constraint1, constraint2, T_max::Real=137//10,
          free::NTuple{2, Bool}=(true, true))
```

Construct an instance of `LinearAMR` from MH constraints at two different lookback times. Each of `constraint1` and `constraint2` should be length-2 indexables (e.g., tuples) whose first element is a metallicity [M/H] and second element is a lookback time in Gyr. The order of the constraints does not matter. 

# Examples

```jldoctest; setup = :(import StarFormationHistories: LinearAMR)
julia> LinearAMR((-2.5, 13.7), (-1.0, 0.0), 13.7) isa LinearAMR{Float64}
true

julia> LinearAMR((-2.5, 13.7), (-1.0, 0.0), 13.7) == LinearAMR((-1.0, 0.0), (-2.5, 13.7), 13.7)
true
```
