Format for supporting the msgpack extension standard.

Built upon the msgpack formats `fixext 1-8` and `ext 8-32`.

## Defaults

Use

```
format(::Type{T}) = ExtensionFormat{I}()
```

or 

```
@pack T in ExtensionFormat{I}
```

to make [`ExtensionFormat`](@ref) with msgpack extension type `I::Int8` the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in [`ExtensionFormat`](@ref), implement

```
destruct(val::T, ::ExtensionFormat{I})::R
```

where the return value `ret::R` must implement `sizeof(ret)` (number of bytes) as well as `write(io, ret)`.

## Unpacking

To support unpacking values of type `T` packed in [`ExtensionFormat`](@ref), implement

```
construct(::Type{T}, ::Vector{UInt8}, ::ExtensionFormat{I})::T
```

or make sure that the constructor `T(::Vector{UInt8})` is defined.
