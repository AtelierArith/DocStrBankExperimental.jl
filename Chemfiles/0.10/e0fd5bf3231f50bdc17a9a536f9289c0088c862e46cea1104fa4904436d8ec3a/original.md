```julia
impropers(topology::Chemfiles.Topology) -> Matrix{UInt64}

```

Get the improper angles in the `topology`, in a `4 x impropers_count(topology)` array.
