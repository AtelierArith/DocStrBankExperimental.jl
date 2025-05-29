```
ProteinStructure{T} <: AbstractVector{ProteinChain{T}}
```

## フィールド

  * `name::String`: 通常は元のファイルの基本名です。
  * `chains::Vector{ProteinChain{T}}`: `ProteinChain`のコレクションです。
  * `atoms::Vector{Atom{T}}`: 構造からの自由な原子で、どのタンパク質残基にも属していません。
