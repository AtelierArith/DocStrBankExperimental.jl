```julia
Residue(
    topology::Chemfiles.Topology,
    index::Integer
) -> Chemfiles.Residue

```

`topology`から`index`の残基のコピーを取得します。

トポロジー内の残基インデックスは、常に残基識別子と同じではありません。
