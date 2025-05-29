Wrapper format for storing the value and type of an object.

If a value `val::T` can be packed in the format `F<:Format` and its type `T` can be packed in [`TypeFormat`](@ref), then packing `val` in `TypedFormat{F}` enables unpacking via `unpack(io, TypedFormat{F}())`, i.e., without knowledge of `T`.
