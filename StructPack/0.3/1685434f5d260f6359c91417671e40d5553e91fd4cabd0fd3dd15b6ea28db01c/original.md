Core format for packing float values.

Built upon the msgpack formats `float 32`, `float 64`.

## Defaults

[`FloatFormat`](@ref) is the default format for `Float16`, `Float32`, and `Float64`. Use

```
format(::Type{T}) = FloatFormat()
```

or

```
@pack T in FloatFormat
```

to make [`FloatFormat`](@ref) the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in [`FloatFormat`](@ref), implement

```
destruct(val::T, ::FloatFormat)::Union{Float16, Float32, Float64}
```

## Unpacking

To support unpacking values of type `T` packed in [`FloatFormat`](@ref),  implement

```
construct(::Type{T}, ::Float64, ::FloatFormat)::T
```

or make sure that the constructor `T(::Float64)` is defined.
