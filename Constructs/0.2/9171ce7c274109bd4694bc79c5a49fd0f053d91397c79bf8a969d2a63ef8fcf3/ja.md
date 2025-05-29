```
IntEnum([T|subcon], E) -> Construct{E}
```

整数型 `T` に基づく（網羅的な）列挙型を定義します。

これは `Base.Enum{T}` のデフォルトコンストラクタです。

# 引数

  * `T<:Integer`: 基になる整数型、デフォルトは `E` の基本型です。
  * `subcon::Construct{T}`: 基になる整数構造体。
  * `E<:Base.Enum`: 列挙型。

# 例

```jldoctest
julia> @enum Fruit::UInt8 apple=1 banana=2 orange=3

julia> deserialize(IntEnum(Fruit), b"\x02")
banana::Fruit = 0x02

julia> deserialize(IntEnum(Fruit), b"\x04")
ERROR: ArgumentError: invalid value for Enum Fruit: 4
[...]

julia> serialize(IntEnum(UInt16le, Fruit), orange)
2-element Vector{UInt8}:
 0x03
 0x00
```
