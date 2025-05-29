```
@bitfield [mutable] struct MyBits
    a:2
    b:3
    _[:3] # padding; width is assumed 1 bit if the length is omitted
    c:1
end
```

Construct a struct representing various fields, with their size specified in bits. The struct can optionally be marked `mutable`.

See also [`@bitflags`](@ref).

# Extended Help

The fields are stored in a compact format where each field only takes up the specified number of bits. Field access gives an unsigned integer, whose lower bits are the bits of the accessed field. The upper bits are zeroed. As a special case, fields with size `1` return a `Bool`. Explicit padding can be specified by naming a field `_`, with freely chosen width. Field names (other than padding) need to be unique. The specified number of bits must be `>= 0`.

The order the fields are given in is the order the fields are stored in. The first field occupies the least significant bits, followed by the second field, up to the last field, which is stored in the most significant bits.

For example, the struct given above has this layout:

| MSB |     |     |     |     |     |     |     | LSB |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|  c  |  _  |  _  |  _  |  b  |  b  |  b  |  a  |  a  |

where `_` is padding, with undefined value.

The constructor created for structs defined with `@bitfield` takes any type in `Union{Int128, Int16, Int32, Int64, Int8, UInt128, UInt16, UInt32, UInt64, UInt8, Bool}` and converts it to the correct size by truncating the upper bits, before storing the truncated value in the object. This truncation also occurs when writing to a field of a mutable object.

!!! warning "Struct size"
    Due to compiler limitations, the size of the resulting object will (currently) always be a multiple of 8 bits. The additional bits added due to this are considered padding and can not be relied on to exist. They may be removed in a future release without notice. If you need padding up to a given size, explicitly specify a trailing padding field.


!!! warning "Field type"
    As there are no variable sized integers in Julia, it is only guaranteed that the return type on field access is large enough to hold all bits required by that field. While currently field sizes larger than `1` return an `UInt`, this is in particular not guaranteed and may be changed in the future, so that e.g. a field of size `2` returns an `UInt8` instead.


# Examples

```jldoctest
julia> @bitfield struct MyBits
           a:2
           b:3
           _:3 # padding
           c:1
       end

julia> bits = MyBits(1,2,3)
MyBits(a: 0x1, b: 0x2, c: true)

julia> bits.a
0x0000000000000001

julia> bits.b
0x0000000000000002

julia> bits.c
true
```
