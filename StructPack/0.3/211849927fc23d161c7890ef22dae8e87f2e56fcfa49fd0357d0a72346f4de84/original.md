Core format for packing binary values.

Built upon the msgpack formats `bin 8`, `bin 16`, `bin 32`.

## Defaults

Use

```
format(::Type{T}) = BinaryFormat()
```

or

```
@pack T in BinaryFormat
```

to make [`BinaryFormat`](@ref) the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in [`BinaryFormat`](@ref), implement

```
destruct(val::T, ::BinaryFormat)::R
```

where the returned value `ret::R` must implement `sizeof(ret)` (number of bytes) as well as `write(io, ret)`.

## Unpacking

To support unpacking values of type `T` packed in [`BinaryFormat`](@ref),  implement

```
construct(::Type{T}, ::Vector{UInt8}, ::BinaryFormat)::T
```

or make sure that the constructor `T(::Vector{UInt8})` is defined.
