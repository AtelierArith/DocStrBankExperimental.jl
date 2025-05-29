```
chains(::Molecule)
chains(::System = default_system(); kwargs...)
```

与えられた原子コンテナのすべてのチェーンを含む `ChainTable{T}` を返します。

# サポートされているキーワード引数

  * `molecule_idx::MaybeInt = nothing`: `nothing` 以外の任意の値は、結果を指定されたIDを持つ分子に属するチェーンに制限します。
