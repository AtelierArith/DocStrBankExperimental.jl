```
transpose!(t::Transposition; waitall=true)
transpose!(dest::PencilArray{T,N}, src::PencilArray{T,N};
           method = Transpositions.PointToPoint())
```

Transpose data from one pencil configuration to the other.

The first variant allows to optionally delay the wait for MPI send operations to complete. This is useful if the caller wants to perform other operations with the already received data. To do this, the caller should pass `waitall = false`, and manually invoke [`MPI.Waitall`](@ref) on the `Transposition` object once the operations are done. Note that this option only has an effect when the transposition method is `PointToPoint`.

See [`Transposition`](@ref) for details.
