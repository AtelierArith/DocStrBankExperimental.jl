```julia
dihedral(
    frame::Chemfiles.Frame,
    i::Integer,
    j::Integer,
    k::Integer,
    m::Integer
) -> Float64

```

四つの直鎖原子によって作られる二面角（ねじれ角）を計算します。
