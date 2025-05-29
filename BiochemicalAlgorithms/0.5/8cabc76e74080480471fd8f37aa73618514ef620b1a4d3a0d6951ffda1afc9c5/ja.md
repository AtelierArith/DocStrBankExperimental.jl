```
secondary_structures(::Molecule)
secondary_structures(::Chain)
secondary_structures(::System; kwargs...)
```

指定された原子コンテナのすべての二次構造を含む `SecondaryStructureTable{T}` を返します。

# サポートされているキーワード引数

  * `molecule_idx::MaybeInt = nothing`
  * `chain_idx::MaybeInt = nothing`

すべてのキーワード引数は、指定されたIDに一致する二次構造に結果を制限します。 `nothing` に設定されたキーワード引数は無視されます。
