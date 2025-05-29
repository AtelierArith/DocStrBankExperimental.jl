Core format for packing map / dictionary values.

Built upon the msgpack formats `fixmap`, `map 16`, `map 32`.

## Defaults

[`MapFormat`](@ref) is the default format for subtypes of `NamedTuple` and `Dict`. Use

```
format(::Type{T}) = MapFormat()
```

or

```
@pack T in MapFormat
```

to make [`MapFormat`](@ref) the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in [`MapFormat`](@ref), implement

```
destruct(val::T, ::MapFormat)::R
```

where the returned value `ret::R` must implement `Base.length(ret)` (number of entries) and must be iterable with key-value pairs as entries. The key / value formats of the entries of `val` are determined via [`keyformat`](@ref) and [`valueformat`](@ref), where `state` is the linear index.

## Unpacking

To support unpacking values of type `T` packed in [`MapFormat`](@ref),  implement

```
construct(::Type{T}, pairs::Generator{T}, ::MapFormat)::T
```

or make sure that the constructor `T(pairs::Generator{T})` is defined (see [`Generator`](@ref)), where `pairs` will contain key-value pairs as entries. The respective types and formats of the keys and values are determined during unpacking via [`keytype`](@ref), [`valuetype`](@ref), [`keyformat`](@ref) and [`valueformat`](@ref), where `state` is the linear index.

!!! warning
    During construction, all entries of the generator `pairs` have to be iterated over. Since `Generator{T}` wraps a lazy map that reads from the IO source to be unpacked, not conducting the iteration before the next object is processed will interfere with unpacking of subsequent values. For the same reason, you should not store the object `pairs` and access it at a later time.

