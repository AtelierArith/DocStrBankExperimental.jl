```
mice(
    mids::Mids;
    iter::Int = 10,
    progressReports::Bool = true,
    kwargs...
    )
```

Adds additional iterations to an existing `Mids` object.

The number of *additional* iterations is specified by `iter`.

`progressReports` can also be specified: all other arguments will be ignored or passed to inner functions.
