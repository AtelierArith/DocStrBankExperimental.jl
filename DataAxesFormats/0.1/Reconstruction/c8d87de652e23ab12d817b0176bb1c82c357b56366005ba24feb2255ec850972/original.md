```
reconstruct_axis!(
    daf::DafWriter;
    existing_axis::AbstractString,
    implicit_axis::AbstractString,
    [rename_axis::Maybe{AbstractString} = nothing,
    empty_implicit::Maybe{StorageScalar} = nothing,
    implicit_properties::Maybe{AbstractSet{<:AbstractString}} = nothing,
    properties_defaults::Maybe{AbstractDict} = nothing]
)::AbstractDict{<:AbstractString, Maybe{StorageScalar}}
```

Given an `existing_axis` in `daf`, which has a property `implicit_axis`, create a new axis with the same name as the property (or, if specified, call it `rename_axis`). If `empty_implicit` is specified, this value of the property is replaced by the empty string (indicate there is no value associated with the `existing_axis` entry). For each of the `implicit_properties`, we collect the mapping between the `implicit_axis` and the property values, and store it as a property of the newly created axis.

If the `implicit_axis` already exists, we verify that all the values provided for it by the `existing_axis` do, in fact, exist as names of entries in the `implicit_axis`. This allows manually creating the `implicit_axis` with additional entries that are not currently in use.

If `implicit_properties` are explicitly specified, then we require the mapping from `implicit_axis` to be consistent. Otherwise, we look at all the properties of the `existing_axis`, and check for each one whether the mapping is consistent; if it is, we migrate the property to the new axis. For example, when importing `AnnData` containing per-cell data, it isn't always clear which property is actually per-batch (e.g., cell age) and which is actually per cell (e.g., doublet score). Not specifying the `implicit_properties` allows the function to figure it out on its own.

!!! note
    For each converted property, the value associated with `existing_axis` entries which have no `implicit_axis` value (that is, have an empty string or `empty_implicit` value) is lost. For example, if each cell type has a color, but some cells do not have a type, then the color of "cells with no type" is lost. We still require this value to be consistent, and return a mapping between each migrated property name and the value of such entries (if any exist). When reconstructing the original property, specify this value using [`IfNot`](@ref) (e.g., `/ cell : type => color ?? magenta`).

