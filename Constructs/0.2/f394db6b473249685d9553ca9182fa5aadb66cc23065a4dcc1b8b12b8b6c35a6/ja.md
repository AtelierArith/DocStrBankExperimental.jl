```
IntEnum{EnumNonExhaustive}([T|subcon], E) -> Construct{E}
```

整数型 `T` に基づく非網羅的列挙型を定義します。

# 引数

  * `T<:Integer`: 基になる整数型、デフォルトは `E` の基本型です。
  * `subcon::Construct{T}`: 基になる整数構造体。
  * `E<:Base.Enum`: 列挙型。

# 例

```jldoctest
julia> @enum Fruit::UInt8 apple=1 banana=2 orange=3

julia> deserialize(IntEnum{EnumNonExhaustive}(Fruit), b"\x04")
<invalid #4>::Fruit = 0x04
```
