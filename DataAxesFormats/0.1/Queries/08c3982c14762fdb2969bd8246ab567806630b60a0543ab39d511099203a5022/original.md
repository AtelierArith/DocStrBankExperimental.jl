```
AsAxis([axis::AbstractString = nothing]) <: QueryOperation
```

There are three cases where we may want to take a vector property and consider each value to be the name of an entry of some axis: [`Fetch`](@ref), [`CountBy`](@ref) and [`GroupBy`](@ref). In a string [`Query`](@ref), this is indicated by the `!` operators, optionally followed by the name of the axis to use.

When using [`Fetch`](@ref), we always lookup in some axis, so [`AsAxis`](@ref) is implied (e.g., `/ cell : type => color` is identical to `/ cell : type ! => color`). In contrast, when using [`CountBy`](@ref) and [`GroupBy`](@ref), one has to explicitly specify `AsAxis` to force using all the entries of the axis for the counting or grouping (e.g., `/ cell : age @ type %> Mean` will return a vector of the mean age of every type that has cells associated with it, while `/ cell : age @ type ! %> Mean` will return a vector of the mean age of each and every value of the type axis; similarly, `/ cell : type * age` will generate a counts matrix whose rows are types that have cells associated with them, while `/ cell : type ! * age` will generate a counts matrix whose rows are exactly the entries of the type axis).

Since the set of values is fixed by the axis matching the vector property, it is possible that, when using this for [`GroupBy`](@ref), some groups would have no values, causing an error. This can be avoided by providing an [`IfMissing`](@ref) suffix to the reduction (e.g., `/ cell : age @ type ! %> Mean` will fail if some type has no cells associated with it, while `/ cell : age @ type ! %> Mean || 0` will give such types a zero mean age).

Typically, the name of the base property is identical to the name of the axis. In this case, there is no need to specify the name of the axis (as in the examples above). Sometimes it is useful to be able to store several vector properties which all map to the same axis. To support this, we support a naming convention where the property name begins with the axis name followed by a `.suffix`. (e.g., both `/ cell : type => color` and `/ cell : type.manual => color` will look up the `color` of the `type` of some property of the `cell` axis - either "the" `type` of each `cell`, or the alternate `type.manual` of each cell).

If the property name does not follow the above conventions, then it is possible to explicitly specify the name of the axis (e.g., `/ cell : manual ! type => color` will consider each value of the `manual` property as the name of an entry of the `type` axis and look up the matching `color` property value of this axis).
