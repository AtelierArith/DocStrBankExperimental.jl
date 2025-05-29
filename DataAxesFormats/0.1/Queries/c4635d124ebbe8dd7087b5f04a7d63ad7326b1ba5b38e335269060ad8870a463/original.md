```
GroupBy(property::AbstractString) <: QueryOperation
```

A query operation that uses a (following) [`ReductionOperation`](@ref) to aggregate the values of each group of values. Will fetch the specified `property_name` (possibly followed by additional [`Fetch`](@ref) operations) and use the resulting vector for the name of the group of each value.

If applied to a vector, the result is a vector with one entry per group (e.g., `/ cell : age @ type %> Mean` will generate a vector with an entry per cell type and whose values are the mean age of the cells of each type). If applied to a matrix, the result is a matrix with one row per group (e.g., `/ cell / gene : UMIs @ type %> Max` will generate a matrix with one row per type and one column per gene, whose values are the maximal UMIs count of the gene in the cells of each type).

By default, the result uses only group values we actually observe, in sorted order. However, if the operation is followed by an [`AsAxis`](@ref) suffix, then the fetched property must correspond to an existing axis (similar to when using [`Fetch`](@ref)), and the result will use the entries of the axis, even if we do not observe them in the data (and will ignore vector entries with an empty value). In this case, the reduction operation will fail if there are no values for some group, unless it is followed by an [`IfMissing`](@ref) suffix (e.g., `/ cell : age @ type ! %> Mean` will generate a vector whose entries are all the entries of the `type` axis, and will ignore cells with an empty type; this will fail if there are types which are not associated with any cell. In contrast, `/ cell : age @ type ! %> Mean || 0` will succeed, assigning a value of zero for types which have no cells associated with them).
