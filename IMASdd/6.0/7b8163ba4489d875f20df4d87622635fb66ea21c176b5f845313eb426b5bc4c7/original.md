```
time_coordinate(@nospecialize(ids::IDS), field::Symbol; error_if_not_time_dependent::Bool)
```

Return index of time coordinate

If `error_if_not_time_dependent == false` it will return `0` for arrays that are not time dependent
