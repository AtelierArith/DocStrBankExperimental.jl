```
Tc = pcsaft_tc(m,ϵ)
```

Returns the critical temperature of the PCSAFT equation of state.

Inputs:

  * `m`: Segment length (no units)
  * `ϵ`: Reduced interaction energy `[K]`

Outputs:

  * `Tc` : Critical Temperature `[K]`.  Returns `NaN` if the value is outside the range of the ancillary (1 ≤ m ≤ 64).

## Examples

```julia-repl
julia> m, ϵ = 1.0, 150.03 #values for methane
(1.0, 150.03)

julia> Tc = pcsaft_tc(m, ϵ)
191.40058128833536
```
