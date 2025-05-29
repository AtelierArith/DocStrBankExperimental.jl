```
Chain{T} <: AbstractAtomContainer{T}
```

システム内の個々のチェーンの可変表現。

# 公開フィールド

  * `idx::Int`
  * `name::String`

# プライベートフィールド

  * `properties::Properties`
  * `flags::Flags`
  * `molecule_idx::Int`

# コンストラクタ

```julia
Chain(
    mol::Molecule{T};
    # キーワード引数
    name::AbstractString = "",
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

指定された分子内に新しい `Chain{T}` を作成します。
