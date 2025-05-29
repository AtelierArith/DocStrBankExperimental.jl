```
pf_adiabatic_signal(envs, ranges, zs, zr; T=2, fs=1000, n_modes=41, t0_offset=0.2)

Calculate the pressure field at a given receiver depth `zr` from a source at `zs`
and using the adiabatic approximation for a range-dependent environment.

Required arguments:
- `envs`: list of underwater environments (Vector{Env})
- `ranges`: ranges of the environments (m)
- `zs`: source depth (m)
- `zr`: receiver depth (m)

Optional keywords:
- `T`: duration of the signal (sec) (default: 2)
- `fs`: sampling frequency (Hz) (default: 1000)
- `n_modes`: number of modes (default: 41)
- `t0_offset`: the signal offset from the beginning of the time window
```
