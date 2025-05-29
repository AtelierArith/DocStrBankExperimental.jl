```
IntEnum{EnumNonExhaustive}([T|subcon], E) -> Construct{E}
```

Defines the non-exhaustive enumeration based on integer type `T`.

# Arguments

  * `T<:Integer`: the underly integer type, default is the base type of `E`.
  * `subcon::Construct{T}`: the underly integer construct.
  * `E<:Base.Enum`: the enum type.

# Examples

```jldoctest
julia> @enum Fruit::UInt8 apple=1 banana=2 orange=3

julia> deserialize(IntEnum{EnumNonExhaustive}(Fruit), b"\x04")
<invalid #4>::Fruit = 0x04
```
