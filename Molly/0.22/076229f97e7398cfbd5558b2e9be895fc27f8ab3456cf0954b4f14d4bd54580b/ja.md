```
StructureWriter(n_steps, filepath, excluded_res=String[])
```

シミュレーション中にPDB形式でファイルに3D構造を書き込みます。

[`System`](@ref)は`atoms_data`が定義されている必要があります。ファイルは追記されるため、シミュレーションの前に既に存在する場合は削除する必要があります。

2Dシステムとは互換性がありません。
