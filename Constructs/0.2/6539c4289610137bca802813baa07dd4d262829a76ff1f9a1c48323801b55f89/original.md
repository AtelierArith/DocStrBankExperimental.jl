```
Padded([T|subcon = Nothing], n) -> Construct{T}
```

Create `n`-bytes padded data from `subcon`.

# Arguments

  * `subcon::Construct{T}`: the construct to be padded.
  * `n::Integer`: the size in bytes after padded.

# Examples

```jldoctest
julia> deserialize(Padded(Int8, 2), b"\x01\xfc")
1

julia> serialize(Padded(Int8, 2), Int8(1))
2-element Vector{UInt8}:
 0x01
 0x00
```
