```julia
bond_orders(
    topology::Chemfiles.Topology
) -> Vector{Chemfiles.BondOrder}

```

`topology`内のすべての結合に対する`BondOrder`を取得します。
