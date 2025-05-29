Pack vectors in binary format.  

Built upon [`BinaryFormat`](@ref).

## Defaults

`BinVectorFormat` is the default format for `BitVector`. Use

```
format(::Type{T}) = BinVectorFormat()
```

or

```
@pack T in BinVectorFormat
```

to make `BinVectorFormat` the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in `BinVectorFormat`, implement

```
destruct(val::T, ::BinVectorFormat)::R
```

where the returned value `ret::R` must be packable in [`BinaryFormat`](@ref).

## Unpacking

To support unpacking values of type `T` packed in `BinVectorFormat`, implement

```
construct(::Type{T}, ::Vector{UInt8}, ::BinVectorFormat)::T
```

or make sure that the constructor `T(bytes::Vector{UInt8})` is defined.
