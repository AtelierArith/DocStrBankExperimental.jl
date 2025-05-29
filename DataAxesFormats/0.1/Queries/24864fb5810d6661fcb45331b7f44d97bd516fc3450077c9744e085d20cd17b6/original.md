```
Fetch(property::AbstractString) <: QueryOperation
```

A query operation for fetching the value of a property from another axis, based on a vector property whose values are entry names of the axis. In a string [`Query`](@ref), this is specified using the `=>` operator, followed by the name to look up.

That is, if you query for the values of a vector property (e.g., `batch` for each `cell`), and the name of this property is identical to some axis name, then we assume each value is the name of an entry of this axis. We use this to fetch the value of some other property (e.g., `age`) of that axis (e.g., `/ cell : batch => age`).

It is useful to be able to store several vector properties which all map to the same axis. To support this, we support a naming convention where the property name begins with the axis name followed by a `.suffix`. (e.g., both `/ cell : type => color` and `/ cell : type.manual => color` will look up the `color` of the `type` of some property of the `cell` axis - either "the" `type` of each `cell`, or the alternate `type.manual` of each cell).

Fetching can be chained (e.g., `/ cell : batch => donor => age` will fetch the `age` of the `donor` of the `batch` of each `cell`).

If the property does not exist, this is an error, unless this is followed by [`IfMissing`](@ref) (e.g., `/ cell : type => color || red`). If the property contains an empty value, this is also an error, unless it is followed by an [`IfNot`](@ref) (e.g., `/ cell : type ? => color` will compute a vector of the colors of the type of the cells that have a non-empty type, and `/ cell : batch ? 0 => donor => age` will assign a zero age for cells which have an empty batch).
