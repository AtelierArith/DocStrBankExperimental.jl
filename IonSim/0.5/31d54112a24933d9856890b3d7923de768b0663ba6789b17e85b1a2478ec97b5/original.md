```
thermalstate(v::VibrationalMode, n̄::Real; method="truncated")
```

Returns a thermal density matrix with $⟨a^†a⟩ ≈ n̄$. Note: approximate because we are dealing with a finite dimensional Hilbert space that must be normalized.

`method` can be set to either `"truncated"` (default) or `"analytic"`. In the former case, the thermal density matrix is generated according to the formula: $ρ_{th} = exp(-νa^†a/T) / Tr [exp(-νa^†a/T)]$. In the later case, the analytic formula, assuming an infinite-dimensional Hilbert space, is used: $[ρ_{th}]_{ij} = δ_{ij} \frac{nⁱ}{(n+1)^{i+1}}.$
