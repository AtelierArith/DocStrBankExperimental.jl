```julia
residue_for_atom(
    topology::Chemfiles.Topology,
    index::Integer
) -> Union{Nothing, Chemfiles.Residue}

```

`topology`内の`index`にある原子を含む残基のコピーを取得します。

この関数は、原子が残基にない場合、または`index`がトポロジー内の原子の数より大きい場合は`nothing`を返します。
