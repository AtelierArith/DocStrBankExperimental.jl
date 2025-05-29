```
Z2Solution{T1,T2,T3} <: TopologicalNumbersSolutions
```

The `Z2Solution` struct represents a solution for calculating Z2 number.

# Fields

  * `TopologicalNumber::T1`: The Z2 number for each pair of energy bands.
  * `TRTopologicalNumber::T2`: The Z2 number for the remaining part of the Brillouin zone. This field is only returned when `TR` is `true` in `Z2Problem`.
  * `Total::T3`: The total Z2 number.
