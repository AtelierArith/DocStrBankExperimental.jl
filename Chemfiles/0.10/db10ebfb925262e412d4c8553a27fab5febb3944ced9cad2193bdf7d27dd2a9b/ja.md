```julia
add_atom!(
    frame::Chemfiles.Frame,
    atom::Chemfiles.Atom,
    position::Vector{Float64}
)
add_atom!(
    frame::Chemfiles.Frame,
    atom::Chemfiles.Atom,
    position::Vector{Float64},
    velocity::Vector{Float64}
)

```

`frame`に`atom`と対応する`position`および`velocity`データを追加します。
