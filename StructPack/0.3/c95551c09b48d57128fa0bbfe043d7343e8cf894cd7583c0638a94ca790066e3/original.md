Core format for packing unsigned integer values.

Built upon the msgpack formats `positive fixint`, `unsigned 8`, `unsigned 16`, `unsigned 32`, `unsigned 64`.

## Defaults

[`UnsignedFormat`](@ref) is the default format of all subtypes of `Unsigned`. Use

```
format(::Type{T}) = UnsignedFormat()
```

or

```
@pack T in UnsignedFormat
```

to make [`UnsignedFormat`](@ref) the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in [`UnsignedFormat`](@ref), implement

```
destruct(val::T, ::UnsignedFormat)::Unsigned
```

## Unpacking

To support unpacking values of type `T` packed in [`UnsignedFormat`](@ref),  implement

```
construct(::Type{T}, ::UInt64, ::UnsignedFormat)::T
```

or make sure that the constructor `T(::UInt64)` is defined.
