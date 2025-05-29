```
split_by_month(var::OutputVar)
```

Split `var` into `OutputVar`s representing months, sorted in chronological order. Each `OutputVar` corresponds to a single month, and the ordering of the `OutputVar`s is determined by the dates of the month. The return type is a vector of `OutputVar`s.

If there are no dates found for a month, then the `OutputVar` for that season will be an empty `OutputVar`. For non-empty `OutputVar`s, the month can be found by `var.attributes["month"]`.

The function will use the start date in `var.attributes["start_date"]`. The unit of time is expected to be second.
