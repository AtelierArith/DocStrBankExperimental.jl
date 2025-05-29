```
ω = pcsaft_acentric(m)
```

Returns the acentric factor of the PCSAFT equation of state.

Inputs:

  * `m`: Segment length (no units)

Outputs:

  * `ω` : acentric factor (no units).  Returns `NaN` if the value is outside the range of the ancillary (1 ≤ m ≤ 64).

## Examples

```julia-repl
julia> m = 1.0
(1.0, 150.03)

julia> Tc = pcsaft_acentric(m)
191.40058128833536
```
