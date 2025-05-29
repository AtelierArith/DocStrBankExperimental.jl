```julia
are_linked(
    topology::Chemfiles.Topology,
    first::Chemfiles.Residue,
    second::Chemfiles.Residue
) -> Bool

```

`topology`からの2つの残基`first`と`second`がリンクされているかどうかを確認します。*すなわち*、最初の残基の1つの原子と2番目の残基の1つの原子の間に結合があるかどうかです。
