```
SimpleQuantity{T<:Number} <: AbstractQuantity{T}
```

スカラー値と物理単位からなる物理量です。

# フィールド

  * `value::T`: 量の値
  * `unit::Unit`: 量の単位

# コンストラクタ

```
SimpleQuantity(::Number, ::AbstractUnit)
SimpleQuantity(::Number)
SimpleQuantity(::AbstractUnit)
```

コンストラクタに単位が渡されない場合、デフォルトで `unitlessUnit` が使用されます。コンストラクタに値が渡されない場合、デフォルトで値は1に設定されます。

引数として `Quantity` が渡された場合、`Quantity` は内部で値を保存するために使用される単位で表現されます。詳細は [`InternalUnits`](@ref) を参照してください。

```
SimpleQuantity(::Quantity)
```

型 `T` が明示的に指定されている場合、Alicorn は `value` をそれに応じて変換しようとします：

```
SimpleQuantity{T}(::Number, ::AbstractUnit) where {T<:Number}
SimpleQuantity{T}(::Number) where {T<:Number}
SimpleQuantity{T}(::AbstractUnit) where {T<:Number}
```

# 例

1. 量 $7\,\mathrm{nm}$（7ナノメートル）は、次のようにコンストラクタメソッドを使用して構築できます：

    ```jldoctest  julia> ucat = UnitCatalogue() ;

    julia> nanometer = ucat.nano * ucat.meter  UnitFactor nm

    julia> quantity = SimpleQuantity(7, nanometer)  7 nm  ```
2. あるいは、$7\,\mathrm{nm}$ は算術的に構築することもできます：

    ```jldoctest  julia> ucat = UnitCatalogue() ;

    julia> nm = ucat.nano * ucat.meter  UnitFactor nm

    julia> quantity = 7nm  7 nm  ```
