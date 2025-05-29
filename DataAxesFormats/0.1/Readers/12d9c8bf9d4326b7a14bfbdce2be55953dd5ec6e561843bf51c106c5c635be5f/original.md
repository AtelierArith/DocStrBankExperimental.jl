The [`DafReader`](@ref) interface specifies a high-level API for reading `Daf` data. This API is implemented here, on top of the low-level [`FormatReader`](@ref) API. The high-level API provides thread safety so the low-level API can (mostly) ignore this issue.

Each data set is given a name to use in error messages etc. You can explicitly set this name when creating a `Daf` object. Otherwise, when opening an existing data set, if it contains a scalar "name" property, it is used. Otherwise some reasonable default is used. In all cases, object names are passed through [`unique_name`](@ref) to avoid ambiguity.

Data properties are identified by a unique name given the axes they are based on. That is, there is a separate namespace for scalar properties, vector properties for each specific axis, and matrix properties for each **unordered** pair of axes.

For matrices, we keep careful track of their [`MatrixLayouts`](@ref). Returned matrices are always in column-major layout, using [`relayout!`](@ref) if necessary. As this is an expensive operation, we'll cache the result in memory. Similarly, we cache the results of applying a query to the data. We allow clearing the cache to reduce memory usage, if necessary.

The data API is the high-level API intended to be used from outside the package, and is therefore re-exported from the top-level `Daf` namespace. It provides additional functionality on top of the low-level [`FormatReader`](@ref) implementation, accepting more general data types, automatically dealing with [`relayout!`](@ref) when needed. In particular, it enforces single-writer multiple-readers for each data set, so the format code can ignore multi-threading and still be thread-safe.

!!! note
    In the APIs below, when getting a value, specifying a `default` of `undef` means that it is an `error` for the value not to exist. In contrast, specifying a `default` of `nothing` means it is OK for the value not to exist, returning `nothing`. Specifying an actual value for `default` means it is OK for the value not to exist, returning the `default` instead. This is in spirit with, but not identical to, `undef` being used as a flag for array construction saying "there is no initializer". If you feel this is an abuse of the `undef` value, take some comfort in that it is the default value for the `default`, so you almost never have to write it explicitly in your code.

