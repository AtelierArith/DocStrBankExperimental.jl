The [`FormatReader`](@ref) and [`FormatWriter`](@ref) interfaces specify a low-level API for storing `Daf` data. To extend `Daf` to support an additional format, create a new implementation of this API.

A storage format object contains some named scalar data, a set of axes (each with a unique name for each entry), and named vector and matrix data based on these axes.

Data properties are identified by a unique name given the axes they are based on. That is, there is a separate namespace for scalar properties, vector properties for each specific axis, and matrix properties for each (ordered) pair of axes.

For matrices, we keep careful track of their [`MatrixLayouts`](@ref). Specifically, a storage format only deals with column-major matrices, listed under the rows axis first and the columns axis second. A storage format object may hold two copies of the same matrix, in both possible memory layouts, in which case it will be listed twice, under both axes orders.

In general, storage format objects are as "dumb" as possible, to make it easier to support new storage formats. The required functions implement a glorified key-value repository, with the absolutely minimal necessary logic to deal with the separate property namespaces listed above.

For clarity of documentation, we split the type hierarchy to [`DafWriter`](@ref) `<:` [`FormatWriter`](@ref) `<:` [`DafReader`](@ref) `<:` [`FormatReader`](@ref).

The functions listed here use the [`FormatReader`](@ref) for read-only operations and [`FormatWriter`](@ref) for write operations into a `Daf` storage. This is a low-level API, not meant to be used from outside the package, and therefore is not re-exported from the top-level `DataAxesFormats` namespace.

In contrast, the functions using [`DafReader`](@ref) and [`DafWriter`](@ref) describe the high-level API meant to be used from outside the package, and are re-exported. These functions are listed in the `DataAxesFormats.Readers` and `DataAxesFormats.Writers` modules. They provide all the logic common to any storage format, allowing us to keep the format-specific functions as simple as possible.

That is, when implementing a new `Daf` storage format, you should write `struct MyFormat <: DafWriter`, and implement the functions listed here for both [`FormatReader`](@ref) and [`FormatWriter`](@ref).
