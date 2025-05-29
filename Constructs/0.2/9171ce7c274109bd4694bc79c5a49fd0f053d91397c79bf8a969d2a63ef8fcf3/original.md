```
IntEnum([T|subcon], E) -> Construct{E}
```

Defines the (exhaustive) enumeration based on integer type `T`.

This is the default constructor for `Base.Enum{T}`.

# Arguments

  * `T<:Integer`: the underly integer type, default is the base type of `E`.
  * `subcon::Construct{T}`: the underly integer construct.
  * `E<:Base.Enum`: the enum type.

# Examples

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
