```
Fragment{T} <: AbstractAtomContainer{T}
```

システム内の個々のフラグメントの可変表現。

# 公開フィールド

  * `idx::Int`
  * `number::Int`
  * `name::String`

# プライベートフィールド

  * `variant::FragmentVariantType`
  * `properties::Properties`
  * `flags::Flags`
  * `molecule_idx::Int`
  * `chain_idx::Int`
  * `secondary_structure_idx::Int`

# コンストラクタ

```julia
Fragment(
    chain::Chain{T},
    number::Int;
    # キーワード引数
    name::AbstractString = "",
    variant::FragmentVariantType = FragmentVariant.None,
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

指定されたチェーン内に新しい `Fragment{T}` を作成します。

```julia
Fragment(
    secondary_structure::SecondaryStructure{T},
    number::Int;
    # キーワード引数
    name::AbstractString = "",
    variant::FragmentVariantType = FragmentVariant.None,
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

指定された二次構造内に新しい `Fragment{T}` を作成します。
