Abstract format type.

Formats determine the rules for packing and unpacking values via msgpack primitives. They are supposed to be singleton types.

To add support for a new format `F <: Format`, define the corresponding methods of [`pack`](@ref) and [`unpack`](@ref).

This package comes with a number of built-in formats. The following core formats have low-level implementations that build upon one or more formats of the msgpack specification:

  * [`NilFormat`](@ref) (msgpack nil),
  * [`BoolFormat`](@ref) (msgpack boolean),
  * [`SignedFormat`](@ref) (msgpack negative / positive fixint, signed 8-64),
  * [`UnsignedFormat`](@ref) (msgpack positive fixint, unsigned 8-64),
  * [`FloatFormat`](@ref) (msgpack float32, float64)
  * [`StringFormat`](@ref) (msgpack fixstr, str 8-32),
  * [`BinaryFormat`](@ref) (msgpack bin 16, bin 32).
  * [`ExtensionFormat`](@ref) (msgpack fixext 1-8, ext 8-32)

For vector-like and map-like objects, several built-in formats with different benefits and drawbacks are provided as subtypes of

  * [`AbstractVectorFormat`](@ref) (msgpack fixarray, array 16, array 32),
  * [`AbstractMapFormat`](@ref) (msgpack fixmap, map 16, map 32).

Additional convenience formats include

  * [`ArrayFormat`](@ref) (store multidimensional arrays),
  * [`BinVectorFormat`](@ref) (store vectors with bitstype elements efficiently),
  * [`BinArrayFormat`](@ref) (store multidimensional bitstype arrays efficiently),
  * [`TypeFormat`](@ref) (store types)
  * [`TypedFormat`](@ref) (store values and their type for generic unpacking).
  * [`ContextFormat`](@ref) (locally enforce a specific context)
