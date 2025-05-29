```
Bond{T} <: AbstractAtomContainer{T}
```

システム内の個々の結合の可変表現。

# 公開フィールド

  * `idx::Int`
  * `a1::Int`
  * `a2::Int`
  * `order::BondOrderType`

# プライベートフィールド

  * `properties::Properties`
  * `flags::Flags`

# コンストラクタ

```julia
Bond(
    ac::AbstractAtomContainer{T} = default_system(),
    a1::Int,
    a2::Int,
    order::BondOrderType;
    # キーワード引数
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

指定された（原子コンテナの）システム内に新しい `Bond{T}` を作成します。

```julia
Bond(
    a1::Atom{T},
    a2::Atom{T},
    order::BondOrderType;
    # キーワード引数
    properties::Properties = Properties(),
    flags::Flags = Flags()
)
```

指定された原子のために新しい `Bond{T}` を作成します。両方の原子は同じシステムに属している必要があります。
