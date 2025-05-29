A date input (`<input type="date">`) - the user can pick a date, the date is returned as `Dates.DateTime` via `@bind`.

Use `default` to set the initial value.

!!! warning "Outdated"
    This is `DateField`, but you should use our new function, [`DatePicker`](@ref), which is much better! It returns a `Date` directly, instead of a `DateTime`.


# Examples

`@bind best_day_of_my_life DateField()`

`@bind best_day_of_my_life DateField(default=today())`

# See also

[`DatePicker`](@ref)
