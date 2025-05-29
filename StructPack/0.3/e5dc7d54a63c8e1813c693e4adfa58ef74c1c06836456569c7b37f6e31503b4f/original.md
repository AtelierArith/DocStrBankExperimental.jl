Core format for packing vector values.

Built upon the msgpack formats `fixarray`, `array 16`, `array 32`.

## Defaults

[`VectorFormat`](@ref) is the default format for subtypes of `Tuple` and `AbstractVector`. Use

```
format(::Type{T}) = VectorFormat()
```

or

```
@pack T in VectorFormat
```

to make [`VectorFormat`](@ref) the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in [`VectorFormat`](@ref), implement

```
destruct(val::T, ::VectorFormat)::R
```

where the returned value `ret::R` must implement `Base.length(ret)` (number of entries) and must be iterable. The formats of the entries of `val` are determined via [`valueformat`](@ref), where `state` is the linear index.

## Unpacking

To support unpacking values of type `T` packed in [`VectorFormat`](@ref),  implement

```
construct(::Type{T}, values::Generator{T}, ::VectorFormat)::T
```

or make sure that the constructor `T(values::Generator{T})` is defined (see [`Generator`](@ref)). The respective types and formats of the entries of `values` are determined via [`valuetype`](@ref) and [`valueformat`](@ref), where `state` is the linear index.

!!! warning
    During construction, all entries of the generator `values` have to be iterated over. Since `Generator{T}` wraps a lazy map that reads from the IO source to be unpacked, not conducting the iteration before the next object is processed will interfere with unpacking of subsequent values. For the same reason, you should not store the object `values` and access it at a later time.

