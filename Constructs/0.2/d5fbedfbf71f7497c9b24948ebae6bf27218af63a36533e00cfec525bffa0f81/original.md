```
Try(T1|subcon1, T2|subcon2, ...) -> Construct{Union{T1, T2, ...}}
Try{TU}(T1|subcon1, T2|subcon2, ...) -> Construct{TU}
```

Try each `subcon` and use the first successful one.

# Examples

Another non-exhaustive enum:

```jldoctest
julia> @enum Fruit::UInt8 apple=1 banana=2 orange=3

julia> deserialize(Try(Fruit, UInt8), b"\x02")
banana::Fruit = 0x02

julia> deserialize(Try(Fruit, UInt8), b"\x04")
0x04
```
