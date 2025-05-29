```julia
ReCreateSelfCons(checkpoint::Dict, F::T, Update::R) :: SelfCons where {T<:Function, R<:Function}
```

Return a `SelfCons` structure from a checkpoint dictionary and the function `F` and `Update` (which are not saved during checkpointing).
