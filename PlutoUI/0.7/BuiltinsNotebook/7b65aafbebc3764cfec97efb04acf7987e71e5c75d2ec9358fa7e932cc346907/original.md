```julia
DatePicker(; [default::Dates.Date])
```

A date input - the user can pick a date, the date is returned as a `Dates.Date`.

Use the `default` keyword argument to set the initial value. If no initial value is given, the bound value is set to `nothing` until a date is picked.

# Examples

```julia
@bind date1 DatePicker()
```

```julia
using Dates

@bind date2 DatePicker(default=Date(2022, 12, 14))
```
