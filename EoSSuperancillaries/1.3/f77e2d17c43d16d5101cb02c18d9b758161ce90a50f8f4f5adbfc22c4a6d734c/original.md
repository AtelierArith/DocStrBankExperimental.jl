```
rhoc = pcsaft_rhoc(m,σ)
```

Returns the critical density of the PCSAFT equation of state.

Inputs:

  * `m`: Segment length (no units)
  * `σ`: Monomer diameter `[m]`

Outputs:

  * `rhoc` : Critical density `[mol/m^3]`. Returns `NaN` if the value is outside the range of the ancillary (1 ≤ m ≤ 64).
