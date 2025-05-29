```julia
TimePicker(; [default::Dates.TimeType], [show_seconds::Bool=false])
```

A time input - the user can pick a time, the time is returned as a `Dates.Time`.

Use the `default` keyword argument to set the initial value. If no initial value is given, the bound value is set to `nothing` until a time is picked.

# Examples

```julia
@bind time1 TimePicker()
```

```julia
import Dates
@bind time2 TimePicker(default=Dates.Time(23,59,44))
```
