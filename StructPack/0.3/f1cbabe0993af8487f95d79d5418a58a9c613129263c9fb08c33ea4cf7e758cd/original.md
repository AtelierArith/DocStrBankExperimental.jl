Core format for packing string values.

Built upon the msgpack formats `fixstr`, `str 8`, `str 16`, `str 32`.

## Defaults

[`StringFormat`](@ref) is the default format for `Symbol` and all subtypes of `AbstractString`. Use

```
format(:: Type{T}) = StringFormat()
```

or

```
@pack T in StringFormat
```

to make [`StringFormat`](@ref) the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in [`StringFormat`](@ref), implement

```
destruct(val::T, ::StringFormat)::R
```

where the returned value `ret::R` must implement `sizeof(ret)` (number of bytes) as well as `write(io, ret)`.

## Unpacking

To support unpacking values of type `T` packed in [`StringFormat`](@ref), implement

```
construct(:: Type{T}, ::String, ::StringFormat)::T
```

or make sure that `convert(T, ::String)` is defined.
