Format for arrays that remembers the array size.

Built upon [`VectorFormat`](@ref).

## Defaults

`ArrayFormat` is the default format for `AbstractArray`. Use

```
format(::Type{T}) = ArrayFormat()
```

or

```
@pack T in ArrayFormat
```

to make `ArrayFormat` the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in `ArrayFormat`, implement

```
destruct(val::T, ::ArrayFormat)::R
```

where the returned value `ret::R` must define `size` and must be packable in [`VectorFormat`](@ref).

## Unpacking

To support unpacking values of type `T` packed in `ArrayFormat`, implement

```
construct(::Type{T}, ::ArrayValue{Generator{T}}, ::ArrayFormat)::T
```

or make sure that the constructor `T(val::ArrayValue{Generator{T}})` is defined (see [`ArrayValue`](@ref) and [`Generator`](@ref)).
