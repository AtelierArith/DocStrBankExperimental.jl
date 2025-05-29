```
dates(var::OutputVar)
```

Return the `date` dimension in `var`.

If `dates` is a dimension, return that.

If not, try computing the dates from the `start_date` and the `times`. In this, we assume `times` is seconds.
