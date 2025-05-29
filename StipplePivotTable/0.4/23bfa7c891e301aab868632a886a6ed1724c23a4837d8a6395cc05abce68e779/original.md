```
pivottable(field::Symbol, args...; kwargs...)
```

Create a pivot table using the specified `field` and additional arguments.

# Arguments

  * `field::Symbol`: The symbol representing the field to be used for the pivot table. Should reference an instance of `PivotTable`.
  * `args...`: Additional positional arguments to be passed to the `st_pivottable` function/component.
  * `kwargs...`: Additional keyword arguments to be passed to the `st_pivottable` function/component.

# Returns

HTML for rendering the pivot table component created by the `st_pivottable` function with the specified configurations.
