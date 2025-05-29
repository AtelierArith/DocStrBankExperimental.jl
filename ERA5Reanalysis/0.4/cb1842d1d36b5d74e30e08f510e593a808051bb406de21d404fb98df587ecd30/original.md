```
ERA5Monthly(;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
    hours :: Bool = false,
) -> ERA5Monthly <: ERA5Dataset or ERA5MonthlyHour <: ERA5Dataset
```

A function that creates an `ERA5Monthly` or `ERA5MonthlyHour` module depending on the input arguments of `hours`.  Data is saved year-by-year.

# Keyword Arguments

  * `path` : The specified directory in which to save the data
  * `start` : The date for which downloads/analysis begins, automatically rounded to the nearest year
  * `stop` : The date for which downloads/analysis finishes, automatically rounded to the nearest year
  * `hours` : If false, download monthly-averaged data. If true, download monthly-averaged data for each hour
