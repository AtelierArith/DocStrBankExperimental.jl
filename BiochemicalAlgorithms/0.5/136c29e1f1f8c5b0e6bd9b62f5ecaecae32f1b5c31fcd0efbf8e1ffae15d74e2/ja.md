```
SecondaryStructure{T} <: AbstractAtomContainer{T}
```

チェーン内の個々の二次構造要素の可変表現。

# 公開フィールド

  * `idx::Int`
  * `number::Int`
  * `type::SecondaryStructureType`
  * `name::String`

# プライベートフィールド

  * `properties::Properties`
  * `flags::Flags`
  * `molecule_idx::Int`
  * `chain_idx::Int`

# コンストラクタ

```julia
SecondaryStructure(
    chain::Chain{T};
    number::Int,
    type::SecondaryStructureType;
    # キーワード引数
    name::AbstractString = "",
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

指定されたチェーン内に新しい `SecondaryStructure{T}` を作成します。
