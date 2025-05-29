Core format for packing signed integer values.

Built upon the msgpack formats `negative fixint`, `positive fixint`, `signed 8`, `signed 16`, `signed 32`, `signed 64`.

## Defaults

[`SignedFormat`](@ref) is the default format of all subtypes of `Signed`. Use

```
format(::Type{T}) = SignedFormat()
```

or

```
@pack T in SignedFormat
```

to make [`SignedFormat`](@ref) the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in [`SignedFormat`](@ref), implement

```
destruct(val::T, ::SignedFormat)::Signed
```

## Unpacking

To support unpacking values of type `T` packed in [`SignedFormat`](@ref), implement

```
construct(::Type{T}, ::Int64, ::SignedFormat)::T
```

or make sure that the constructor `T(::Int64)` is defined.
