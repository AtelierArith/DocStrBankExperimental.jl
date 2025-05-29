```julia
Lattice(
    height::Int64,
    max_height::Int64,
    min_height::Int64
) -> ActinRingsMC.Lattice

```

2D lattice with periodic conditions on y.

The max and min heights should be calculated based on the number of scaffold filaments and the length of the filaments.
