```
ArrowTypes.ArrowKind(T)
```

For a give type `T`, define it's "arrow type kind", or the general category of arrow types it should be treated as. Must be one of:

  * [`ArrowTypes.NullKind`](@ref): `Missing` is the only type defined as `NullKind`
  * [`ArrowTypes.PrimitiveKind`](@ref): `<:Integer`, `<:AbstractFloat`, along with `Arrow.Decimal`, and the various `Arrow.ArrowTimeType` subtypes
  * [`ArrowTypes.BoolKind`](@ref): only `Bool`
  * [`ArrowTypes.ListKind`](@ref): any `AbstractString` or `AbstractArray`
  * [`ArrowTypes.FixedSizeList`](@ref): `NTuple{N, T}`
  * [`ArrowTypes.MapKind`](@ref): any `AbstractDict`
  * [`ArrowTypes.StructKind`](@ref): any `NamedTuple` or plain struct (mutable or otherwise)
  * [`ArrowTypes.UnionKind`](@ref): any `Union`
  * [`ArrowTypes.DictEncodedKind`](@ref): array types that implement the `DataAPI.refarray` interface

The list of `ArrowKind`s listed above translate to different ways to physically store data as supported by the arrow data format. See the docs for each for an idea of whether they might be an appropriate fit for a custom type. Note that custom types need to satisfy any additional "interface methods" as required by the various `ArrowKind` types. By default, if a type in julia is declared like `primitive type ...` it is considered a `PrimitiveKind` and if `struct` or `mutable struct` it's considered a `StructKind`. Also note that types will rarely need to define `ArrowKind`; much more common is to define `ArrowType(T)` and `toarrow(x::T)` to transform `T` to a natively supported arrow type, which will already have its `ArrowKind` defined.
