```
struct ShuffleCodec <: Codec
ShuffleCodec(element_size::Integer)
```

Byte shuffle. The element size is required to be able to decode the shuffle.

For example:

```julia
[
0x11, 0x12, 0x13,
0x21, 0x22, 0x23,
0x31, 0x32, 0x33,
0x41, 0x42, 0x43,
]
```

with element size 3 will be encoded as

```julia
[
0x11, 0x21, 0x31, 0x41,
0x12, 0x22, 0x32, 0x42,
0x13, 0x23, 0x33, 0x43,
]
```

If the length of the data is not evenly divisible by the element size, the remainder data is appended.

For example "12312312312345" with element size 3 will be encoded as "11112222333345"

A `ShuffleCodec` can be used as an encoder or decoder.
