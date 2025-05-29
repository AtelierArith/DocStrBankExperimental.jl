```
fragments(::SecondaryStructureTable)
fragments(::ChainTable)
fragments(::MoleculeTable)
```

指定されたテーブルのすべてのフラグメントを含む `FragmentTable{T}` を返します。

# サポートされているキーワード引数

  * `variant::Union{Nothing, FragmentVariantType} = nothing` `nothing` 以外の任意の値は、結果を一致するバリアントタイプに制限します。
