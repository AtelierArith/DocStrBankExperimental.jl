```
nbonds(::Chain)
nbonds(::Fragment)
nbonds(::Molecule)
nbonds(::System = default_system())
```

指定された原子コンテナ内で、少なくとも1つの関連原子が同じコンテナに含まれている場合の結合の数を返します。

# サポートされているキーワード引数

[`atoms`](@ref)を参照してください。
