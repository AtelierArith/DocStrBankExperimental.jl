```
BoseFSIndex
```

Struct used for indexing and performing [`excitation`](@ref)s on a [`BoseFS`](@ref).

## Fields:

  * `occnum`: the occupation number.
  * `mode`: the index of the mode.
  * `offset`: the position of the mode in the address. This is the bit offset of the mode when

the address is represented by a bitstring, and the position in the list when it is  represented by `SortedParticleList`.
