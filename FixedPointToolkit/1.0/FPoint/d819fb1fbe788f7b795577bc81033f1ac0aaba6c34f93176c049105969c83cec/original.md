```julia
ContinueFixedPoint!(fileName::String, F::T, Update::R) where {T<:Function, R<:Function}
```

Reruns a fixed point iteration on the `SelfCons` reconstructed from the checkpoint saved in the JLD2 file `fileName`.
