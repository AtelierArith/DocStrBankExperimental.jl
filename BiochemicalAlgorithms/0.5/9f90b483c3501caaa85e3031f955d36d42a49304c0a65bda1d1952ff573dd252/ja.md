```
Molecule{T} <: AbstractAtomContainer{T}
```

システム内の個々の分子の可変表現。

# 公開フィールド

  * `idx::Int`
  * `name::String`

# プライベートフィールド

  * `variant::MoleculeVariantType`
  * `properties::Properties`
  * `flags::Flags`

# コンストラクタ

```julia
Molecule(
    sys::System{T};
    # キーワード引数
    name::AbstractString = "",
    variant::MoleculeVariantType = MoleculeVariant.None,
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

指定されたシステム内に新しい `Molecule{T}` を作成します。

```julia
Molecule(;
    #キーワード引数
    name::AbstractString = "",
    variant::MoleculeVariantType = MoleculeVariant.None,
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

デフォルトのシステム内に新しい `Molecule{Float32}` を作成します。
