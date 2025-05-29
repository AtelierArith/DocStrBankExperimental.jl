Format that is used for packing types.

In order to pack and unpack a type `T::Type` in `TypeFormat`, make sure that `t = StructPack.TypeValue(T)` works and that `StructPack.composetype(t)` successfully reconstructs `T`.

If `T` has type parameters, their serialization can be influenced via the functions [`typeparamtypes`](@ref) and [`typeparamformats`](@ref).

By default, all type parameters are packed / unpacked in [`TypedFormat`](@ref).
