```julia
evaluate(
    selection::Chemfiles.Selection,
    frame::Chemfiles.Frame
) -> Vector{Any}

```

Evaluate a `selection` on a given `frame`. This function return a list of indexes or tuples of indexes of atoms in the frame matching the selection.
