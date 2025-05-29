```
vc = pcsaft_vc(m,σ)
```

Returns the critical volume of the PCSAFT equation of state. Equal to `1/pcsaft_rhoc(m,ϵ,σ)`

Inputs:

  * `m`: Segment length (no units)
  * `σ`: Monomer diameter `[m]`

Outputs:

  * `vc` : Critical volume `[m^3/mol]`. Returns `NaN` if the value is outside the range of the ancillary (1 ≤ m ≤ 64).
