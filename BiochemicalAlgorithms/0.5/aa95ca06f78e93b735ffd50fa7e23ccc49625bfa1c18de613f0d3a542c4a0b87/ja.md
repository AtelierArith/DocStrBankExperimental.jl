```
bonds(::Chain)
bonds(::Fragment)
bonds(::Molecule)
bonds(::System = default_system())
```

指定された原子コンテナ内のすべての結合を含む `BondTable{T}` を返します。少なくとも1つの関連原子が同じコンテナに含まれている必要があります。

# サポートされているキーワード引数

[`atoms`](@ref) を参照してください。
