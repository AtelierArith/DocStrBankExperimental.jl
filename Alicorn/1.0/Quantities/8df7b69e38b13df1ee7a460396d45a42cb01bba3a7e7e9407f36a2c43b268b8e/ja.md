```
Quantity{T<:Number} <: AbstractQuantity{T}
```

数値、物理的次元を表す `Dimension` オブジェクト、および SI システムの七つの基本次元に対して測定される単位を表す `InternalUnits` オブジェクトから構成される物理量。

`Quantity{T}` の値フィールドは型 `T` であり、これは `Number` のサブタイプである必要があります。

# フィールド

  * `value::T`: 量の値
  * `dimension::Dimension`: 量の物理的次元
  * `internalUnits::InternalUnits`: SI システムの七つの基本次元に対して測定される単位のセット

# コンストラクタ

コンストラクタは、内部単位への変換時に可能な限り値の型 `T` を保持します。コンストラクタに `InternalUnits` が渡されない場合、基本 SI 単位がデフォルトで使用されます。

値と次元からの構築; コンストラクタに次元が渡されない場合、デフォルトで無次元量が構築されます。

```
Quantity(::Number, ::Dimension, ::InternalUnits)
Quantity(::Number, ::Dimension)
Quantity(::Number, ::InternalUnits)
Quantity(::Number)
```

型 `T` が明示的に指定されている場合、Alicorn は `value` をそれに応じて変換しようとします：

```
Quantity{T}(::Number, ::Dimension, ::InternalUnits) where {T<:Number}
Quantity{T}(::Number, ::Dimension) where {T<:Number}
Quantity{T}(::Number, ::InternalUnits) where {T<:Number}
Quantity{T}(::Number) where {T<:Number}
```

値と単位からの構築; コンストラクタに単位が渡されない場合、デフォルトで無次元量が構築されます。

```
Quantity(::Number, ::AbstractUnit, ::InternalUnits)
Quantity(::Number, ::AbstractUnit)
Quantity(::AbstractUnit, ::InternalUnits)
Quantity(::AbstractUnit)
```

# 例

1. 量 $7\,\mathrm{nm}$（7ナノメートル）は、次のように構築できます：

    ```jldoctest  julia> ucat = UnitCatalogue() ;         nm = ucat.nano*ucat.meter;         intu = InternalUnits(length=1nm) ;

    julia> Quantity(7nm, intu)  Quantity{Int64} of dimension L^1 in units of (1 nm):   7  ```

    値の元の型 `Int64` が保持されていることに注意してください。
2. 長さの内部単位として $2\,\mathrm{nm}$ を使用すると、値はもはや内部的に型 `Int64` として表現できなくなります：

    ```jldoctest  julia> ucat = UnitCatalogue() ;         nm = ucat.nano*ucat.meter;         intu = InternalUnits(length=2nm) ;

    julia> Quantity(7nm, intu)  Quantity{Float64} of dimension L^1 in units of (2 nm):   3.5  ```
