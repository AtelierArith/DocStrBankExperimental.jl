```
OutputVar(path,
          short_name = nothing;
          new_start_date = nothing,
          shift_by = identity)
```

Read the NetCDF file in `path` as an `OutputVar`.

If `short_name` is `nothing`, automatically find the name.

Dates in the time dimension are automatically converted to seconds with respect to the first date in the time dimension array or the `new_start_date`. The parameter `new_start_date` can be any string parseable by the [Dates](https://docs.julialang.org/en/v1/stdlib/Dates/) module or a `Dates.DateTime` object. The parameter `shift_by` is a function that takes in Dates.DateTime elements and return Dates.DateTime elements. The start date is added to the attributes of the `OutputVar`. The parameter `shift_by` is a function that takes in `Dates.DateTime` elements and returns `Dates.DateTime` elements. This function is applied to each element of the time array. Shifting the dates and converting to seconds is done in that order.
