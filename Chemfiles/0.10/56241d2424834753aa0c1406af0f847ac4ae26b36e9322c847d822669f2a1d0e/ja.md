```julia
add_bond!(
    topology::Chemfiles.Topology,
    i::Integer,
    j::Integer
)
add_bond!(
    topology::Chemfiles.Topology,
    i::Integer,
    j::Integer,
    order
)

```

`topology`内の原子`i`と`j`の間に結合を追加し、オプションで結合の`order`を設定します。
