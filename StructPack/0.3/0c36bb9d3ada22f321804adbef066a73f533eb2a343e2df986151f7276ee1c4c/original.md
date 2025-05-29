Pack arrays in binary format.  

Built upon [`BinVectorFormat`](@ref).

## Defaults

`BinArrayFormat` is the default format for `BitArray{N}` for `N > 1`. Use

```
format(::Type{T}) = BinArrayFormat()
```

or

```
@pack T in BinArrayFormat
```

to make `BinVectorFormat` the default format for type `T`. If `T` is abstract, use `{<: T}` to cover all subtypes.

## Packing

To support packing values of type `T` in `BinArrayFormat`, implement

```
destruct(val::T, ::BinArrayFormat)::R
```

where the returned value `ret::R` must define `Base.size` and must be packable in [`BinaryFormat`](@ref).

## Unpacking

To support unpacking values of type `T` packed in `BinArrayFormat`, implement

```
construct(::Type{T}, ::BinArrayValue{Vector{UInt8}}, ::BinArrayFormat)::T
```

or make sure that the constructor `T(val::BinArrayValue{Vector{UInt8}})` is defined (see [`BinArrayValue`(@ref)]).
