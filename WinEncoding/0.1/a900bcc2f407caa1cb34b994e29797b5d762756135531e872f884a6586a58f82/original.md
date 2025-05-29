```
decode950(a::Vector{UInt8})
```

Convert an array of bytes `a` representing text in encoding `cp950/big5/hkscs` to a string.

  * fallback to big5-hkscs or '�';no invalid sequence error
  * non-blocking

    decode950(f::Filename)

Convert file `f` content to Vector{UInt8} from cp950 to utf-8

## Examples

```jldoctest
julia> decode950([0xa4,0x48])
"人"
```
