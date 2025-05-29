```julia
remove_bond!(
    topology::Chemfiles.Topology,
    i::Integer,
    j::Integer
)

```

`topology`内の原子`i`と`j`の間に存在する任意の結合を削除します。
