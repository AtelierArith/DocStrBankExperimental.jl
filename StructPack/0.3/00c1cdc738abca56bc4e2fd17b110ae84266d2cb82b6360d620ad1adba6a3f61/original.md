Modification of [`StructFormat`](@ref).

When unpacking a value in map format, this format ignores superfluous fields and supports reading only a subset of the fields of a struct.

By default, the keyword argument based constructor `T(; pairs...)` is used when unpacking a type `T` in [`FlexibleStructFormat`](@ref), where `pairs` denotes the entries unpacked from the msgpack map.
