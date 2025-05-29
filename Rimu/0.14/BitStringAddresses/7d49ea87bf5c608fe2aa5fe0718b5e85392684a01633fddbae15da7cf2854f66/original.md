```
FermiFSIndex
```

Struct used for indexing and performing [`excitation`](@ref)s on a [`FermiFS`](@ref).

## Fields:

  * `occnum`: the occupation number.
  * `mode`: the index of the mode.
  * `offset`: the position of the mode in the address. This is `mode - 1` when the address is represented by a bitstring, and the position in the list when using `SortedParticleList`.
