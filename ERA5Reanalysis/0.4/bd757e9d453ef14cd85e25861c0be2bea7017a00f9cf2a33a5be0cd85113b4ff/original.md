```
ERA5Hourly(;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> ERA5Hourly <: ERA5Dataset
```

A function that creates an `ERA5Hourly` module.  All possible hours are downloaded, and data is saved month-by-month.

# Keyword Arguments

  * `path` : The specified directory in which to save the data
  * `start` : The date for which downloads/analysis begins, automatically rounded to the nearest month
  * `stop` : The date for which downloads/analysis finishes, automatically rounded to the nearest month
