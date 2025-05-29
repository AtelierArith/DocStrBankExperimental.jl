Core format for packing nil values.

Built upon the msgpack format `nil`.

## Defaults

[`NilFormat`](@ref) is the default format of `Nothing`. Use

```
format(::Type{T}) = NilFormat()
```

or

```
@pack T in NilFormat
```

to make [`NilFormat`](@ref) the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

All types can be packed in [`NilFormat`](@ref).

## Unpacking

To support unpacking values of type `T` packed in [`NilFormat`](@ref), implement

```
construct(::Type{T}, ::Nothing, ::NilFormat)::T
```

or make sure that the constructor `T()` is defined.
