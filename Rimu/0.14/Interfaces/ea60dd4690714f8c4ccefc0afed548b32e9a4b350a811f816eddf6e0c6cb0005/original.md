```
localpart(dv) -> AbstractDVec
```

Get the part of `dv` that is located on this MPI rank. Returns `dv` itself for vectors that can't be MPI distributed ([`DVec`](@ref Main.DictVectors.DVec)s and [`InitiatorDVec`](@ref Main.DictVectors.InitiatorDVec)s).
