```julia
mutable struct System{T} <: BiochemicalAlgorithms.AbstractAtomContainer{T}
```

バイオ分子システムの可変表現。

# フィールド

  * `name::String`
  * `properties::Properties`
  * `flags::Flags`

# コンストラクタ

```
System(name::AbstractString = "", properties::Properties = Properties(), flags::Flags = Flags())
```

新しい空の `System{Float32}` を作成します。

```
System{T}(name::AbstractString = "", properties::Properties = Properties(), flags::Flags = Flags())
```

新しい空の `System{T}` を作成します。
