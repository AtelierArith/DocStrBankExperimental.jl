Core format for packing boolean values.

Built upon the msgpack format `boolean`.

## Defaults

[`BoolFormat`](@ref) is the default format of `Bool`. Use

```
format(::Type{T}) = BoolFormat()
```

or

```
@pack T in BoolFormat
```

to make [`BoolFormat`](@ref) the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in [`BoolFormat`](@ref), implement

```
destruct(val::T, ::BoolFormat)::Bool
```

## Unpacking

To support unpacking values of type `T` packed in [`BoolFormat`](@ref), implement

```
construct(::Type{T}, ::Bool, ::BoolFormat)::T
```

or make sure that the constructor `T(::Bool)` is defined.
