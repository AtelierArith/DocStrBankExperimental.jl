```
Atom{T} <: AbstractSystemComponent{T}
```

システム内の個々の原子の可変表現。

# 公開フィールド

  * `idx::Int`
  * `number::Int`
  * `element::ElementType`
  * `name::String`
  * `atom_type::String`
  * `r::Vector3{T}`
  * `v::Vector3{T}`
  * `F::Vector3{T}`
  * `formal_charge::Int`
  * `charge::T`
  * `radius::T`

# プライベートフィールド

  * `properties::Properties`
  * `flags::Flags`
  * `frame_id::Int`
  * `molecule_idx::MaybeInt`
  * `chain_idx::MaybeInt`
  * `fragment_idx::MaybeInt`

# コンストラクタ

```julia
Atom(
    ac::AbstractAtomContainer{T}
    number::Int,
    element::ElementType;
    # キーワード引数
    name::AbstractString = "",
    atom_type::AbstractString = "",
    r::Vector3{T} = Vector3{T}(0, 0, 0),
    v::Vector3{T} = Vector3{T}(0, 0, 0),
    F::Vector3{T} = Vector3{T}(0, 0, 0),
    formal_charge::Int = 0,
    charge::T = zero(T),
    radius::T = zero(T),
    properties::Properties = Properties(),
    flags::Flags = Flags(),
    frame_id::Int = 1
    molecule_idx::MaybeInt = nothing,
    chain_idx::MaybeInt = nothing,
    fragment_idx::MaybeInt = nothing
)
```

指定された原子コンテナ内に新しい `Atom{T}` を作成します。

```julia
Atom(
    number::Int,
    element::ElementType;
    kwargs...
)
```

デフォルトシステム内に新しい `Atom{Float32}` を作成します。上記と同じキーワード引数をサポートします。
