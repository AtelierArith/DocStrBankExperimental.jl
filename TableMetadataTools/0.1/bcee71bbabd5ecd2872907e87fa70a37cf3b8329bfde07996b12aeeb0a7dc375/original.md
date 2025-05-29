```
unit!(table, column, unit)
```

Store representation of `unit` as value of `"unit"` key with `:note`-style as column-level metadata for column `column` in `table` that must be compatible with Tables.jl table interface. Any value is accepted for user convenience, however `Unitful.Units` unit is recommended.

Note that if element type of column `column` is `Unitful.Quantity` or `Dates.FixedPeriod` then setting unit is not needed (but can be done to override the default unit).

See also: [`unit`](@ref), [`units`](@ref)
