```
concatenate!(
    destination::DafWriter,
    axis::Union{AbstractString, AbstractVector{<:AbstractString}},
    sources::AbstractVector{<:DafReader};
    [names::Maybe{AbstractVector{<:AbstractString}} = nothing,
    dataset_axis::Maybe{AbstractString} = "dataset",
    dataset_property::Bool = true,
    prefix::Union{Bool, AbstractVector{Bool}} = false,
    prefixed::Maybe{Union{AbstractSet{<:AbstractString}, AbstractVector{<:AbstractSet{<:AbstractString}}}} = nothing,
    empty::Maybe{EmptyData} = nothing,
    sparse_if_saves_storage_fraction::AbstractFloat = 0.25,
    merge::Maybe{MergeData} = nothing,
    overwrite::Bool = false]
)::Nothing
```

Concatenate data from a `sources` sequence of `Daf` data sets into a single `destination` data set along one or more concatenation `axis`. You can also concatenate along multiple axes by specifying an array of `axis` names.

We need a unique name for each of the concatenated data sets. By default, we use the `DafReader.name`. You can override this by specifying an explicit `names` vector with one name per data set.

By default, a new axis named by `dataset_axis` is created with one entry per concatenated data set, using these unique names. You can disable this by setting `dataset_axis` to `nothing`.

If an axis is created, and `dataset_property` is set (the default), a property with the same name is created for the concatenated `axis`, containing the name of the data set each entry was collected from.

The entries of each concatenated axis must be unique. By default, we require that no entry name is used in more than one data set. If this isn't the case, then set `prefix` to specify adding the unique data set name (and a `.` separator) to its entries (either once for all the axes, or using a vector with a setting per axis).

!!! note
    If a prefix is added to the axis entry names, then it must also be added to all the vector properties whose values are entries of the axis. By default, we assume that any property name that is identical to the axis name is such a property (e.g., given a `cluster` axis, a `cluster` property of each `cell` is assumed to contain the names of clusters from that axis). We also allow for property names to just start with the axis name, followed by `.` and some suffix (e.g., `cluster.manual` will also be assumed to contain the names of clusters). We'll automatically add the unique prefix to all such properties.

    If, however, this heuristic fails, you can specify a vector of properties to be `prefixed` (or a vector of such vectors, one per concatenated axis). In this case only the listed properties will be prefixed with the unique data set names.


Vector and matrix properties for the `axis` will be concatenated. If some of the concatenated data sets do not contain some property, then an `empty` value must be specified for it, and will be used for the missing data.

Concatenated matrices are always stored in column-major layout where the concatenation axis is the column axis. There should not exist any matrices whose both axes are concatenated (e.g., square matrices of the concatenated axis).

The concatenated properties will be sparse if the storage for the sparse data is smaller than naive dense storage by at `sparse_if_saves_storage_fraction` (by default, if using sparse storage saves at least 25% of the space, that is, takes at most 75% of the dense storage space). When estimating this fraction, we assume dense data is 100% non-zero; we only take into account data already stored as sparse, as well as any missing data whose `empty` value is zero.

By default, properties that do not apply to any of the concatenation `axis` will be ignored. If `merge` is specified, then such properties will be processed according to it. Using `CollectAxis` for a property requires that the `dataset_axis` will not be `nothing`.

By default, concatenation will fail rather than `overwrite` existing properties in the target.
