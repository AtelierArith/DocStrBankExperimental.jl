```julia
out_of_plane(
    frame::Chemfiles.Frame,
    i::Integer,
    j::Integer,
    k::Integer,
    m::Integer
) -> Float64

```

4つの原子によって形成される面外（不適切）角を計算します。
