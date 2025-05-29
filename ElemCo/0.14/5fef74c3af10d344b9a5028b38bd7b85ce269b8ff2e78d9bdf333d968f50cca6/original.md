```
@bohf()
```

Run bi-orthogonal HF calculation using FCIDUMP integrals.

The orbitals are stored to [`WfOptions.orb`](@ref ECInfos.WfOptions).   For open-shell systems (or UHF FCIDUMPs), the BO-UHF energy is calculated.

# Examples

```julia
fcidump = "FCIDUMP"
@bohf
```
