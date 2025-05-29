```
pf_adiabatic(freq, envs, ranges, zs, zr; n_modes = 41)
```

Calculate the adiabatic pressure field for a given frequency.

Required arguments:

  * `freq`: frequency (Hz)
  * `envs`: list of underwater environments (Vector{Env})
  * `ranges`: ranges of the environments (m)
  * `zs`: source depth (m)
  * `zr`: receiver depth (m)
