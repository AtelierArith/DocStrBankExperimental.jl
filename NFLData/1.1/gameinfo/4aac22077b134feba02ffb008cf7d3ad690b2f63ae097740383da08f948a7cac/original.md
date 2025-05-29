```
get_current_week(use_date::Bool = false)
```

Return the current/upcoming week of the NFL season. Uses the schedules by default, can be swapped to use date-based heuristics by passing `use_date=true`.

# Examples

```julia
julia>  # if using Dates; today() == "2024-09-15"

julia>get_current_week()
2
```
