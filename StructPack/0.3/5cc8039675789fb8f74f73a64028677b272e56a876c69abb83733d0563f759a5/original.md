Format for packing structures.

Built upon the msgpack formats `fixmap`, `map 16`, `map 32`.

## Defaults

[`StructFormat`](@ref) is not used as default for any type. However, it should be the first candidate when you want to pack custom structs. Use

```
format(::Type{T}) = StructFormat()
```

or

```
@pack T in StructFormat
```

to make [`StructFormat`](@ref) the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in [`StructFormat`](@ref), implement

```
destruct(val::T, ::MapFormat)::R
```

where the returned value `ret::R` must implement `Base.length(ret)` (number of entries) and must be iterable with key-value pairs as entries.

In contrast to [`MapFormat`](@ref), the keys are always stored in [`StringFormat`](@ref) and the value formats are determined via [`fieldformats`](@ref), which should return a tuple of formats for the value-entries of the struct.

## Unpacking

To support unpacking values of type `T` packed in [`StructFormat`](@ref),  implement

```
construct(::Type{T}, pairs::Generator{T}, ::StructFormat)::T
```

or make sure that the constructor `T(values...)` is defined, where `values` contains the value-entries of `pairs`.

The respective types and formats of the values are determined during unpacking via [`fieldtypes`](@ref) and [`fieldformats`](@ref), which should return tuples of types and formats. Additionally, [`fieldnames`](@ref) is queried to make sure the keys encountered during unpacking are consistent with `T`.

!!! note "StructFormat vs. MapFormat"
    Both [`StructFormat`](@ref) and [`MapFormat`](@ref) can be used to pack custom structs. They perform comparably.

      * [`MapFormat`](@ref) is more flexible and can handle keys that are not symbols. In contrast, [`StructFormat`](@ref) requires static fieldtype, fieldname, and fieldformat information.
      * However, [`MapFormat`](@ref) will not counter-check key values during unpacking and can thus easily lead to corrupted data if applied on external msgpack binaries.

