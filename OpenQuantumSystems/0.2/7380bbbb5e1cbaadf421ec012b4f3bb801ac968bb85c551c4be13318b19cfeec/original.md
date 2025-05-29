```
Molecule{T,C1,C2}(modes, Nvib, E)
```

Stuct which purpose is to model a molecule in [`Aggregate`](@ref).

# Arguments

  * `modes`: Vector of modes ([`Mode`](@ref)).
  * `Nvib`: Maximum number of vibrational states for all modes.
  * `E`: Energy of ground and excited state of molecule (HOMO, LUMO).
