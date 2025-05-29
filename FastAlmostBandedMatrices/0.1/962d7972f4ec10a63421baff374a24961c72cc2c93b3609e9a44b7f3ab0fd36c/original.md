```
AlmostBandedMatrix(bands::BandedMatrix, fill)
AlmostBandedMatrix{T}(bands, fill)
AlmostBandedMatrix(::UndefInitializer, [::Type{T} = Float64], mn::NTuple{2, Integer},
    lu::NTuple{2, Integer}, rank::Integer)
AlmostBandedMatrix{T}(::UndefInitializer, mn::NTuple{2, Integer},
    lu::NTuple{2, Integer}, rank::Integer)
```

An `AlmostBandedMatrix` is a matrix with a `bands` part and a `fill` part. For efficient operations we store the matrix as a BandedMatrix and another AbstractMatrix with an overlapping bit.

[3 3 3 2 2 2 2 ... 2 2 2]
[3 3 3 3 2 2 2 ... 2 2 2]
[0 1 1 1 1 0 0 ... 0 0 0]
[0 0 1 1 1 1 0 ... 0 0 0]
[.......................]
[.......................]
[.......................]
[0 0 0 0 0 0 0 ... 1 1 0]
[0 0 0 0 0 0 0 ... 1 1 1]

where `2`'s are the fill part, and `1`'s are the bands part, and `3`'s are the overlapping part.
