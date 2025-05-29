```
atoms(::Chain)
atoms(::Fragment)
atoms(::Molecule)
atoms(::System = default_system())
```

指定された原子コンテナのすべての原子を含む `AtomTable{T}` を返します。

# サポートされているキーワード引数

  * `frame_id::MaybeInt = 1`
  * `molecule_idx::Union{MaybeInt, Some{Nothing}} = nothing`
  * `chain_idx::Union{MaybeInt, Some{Nothing}} = nothing`
  * `fragment_idx::Union{MaybeInt, Some{Nothing}} = nothing`

すべてのキーワード引数は、指定されたIDに一致する原子に結果を制限します。 `nothing` に設定されたキーワード引数は無視されます。 `Some(nothing)` を使用して、`nothing` のID値を明示的にフィルタリングできます。
