```julia
bond_order(
    topology::Chemfiles.Topology,
    i::Integer,
    j::Integer
) -> Chemfiles.BondOrder

```

`topology`内の原子`i`と`j`の間の結合に対する`BondOrder`を取得します。
