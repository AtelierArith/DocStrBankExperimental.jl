```
DMHybridization(id::Symbol, value, bondkind; amplitude::Union{Function, Nothing}=nothing, ismodulatable::Union{Function, Bool}=true)
```

The DM Magnon-Phonon coupling term.

Type alias for `Term{:DMHybridization, id, V, B, C<:TermCoupling, A<:TermAmplitude}`
