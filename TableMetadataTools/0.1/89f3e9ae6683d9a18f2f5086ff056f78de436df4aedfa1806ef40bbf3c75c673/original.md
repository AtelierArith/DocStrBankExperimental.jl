```
unit(table, column)
```

Return representation of the value of the `"unit"` column-level metadata of column `column` in `table` that must be compatible with Tables.jl table interface.

If `"unit"` column-level metadata for column `column` is missing and element type of the column is `Units.Quantity` or `Dates.FixedPeriod` return unit of this type. If element type is `Number` return `Unitful.NoUnits`. Union with `Missing` is allowed in the above cases. For all other cases return `missing`.

Warning! The proposed definition of `unit` is type piracy, but it is made for user convenience. It works under the assumption that other methods for `unit` (defined in other packages) always take one positional argument. If this assumption would not hold in the future the definition of `unit` in this package might change.

See also: [`unit!`](@ref), [`units`](@ref) ```
