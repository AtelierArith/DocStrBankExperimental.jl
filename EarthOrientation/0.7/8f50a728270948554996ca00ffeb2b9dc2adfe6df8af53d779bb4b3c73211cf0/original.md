```
getlod_err(date; outside_range=:warn)
```

Get the error in the excess length of day for a certain `date` in milliseconds.

`date` can either be a `DateTime` object or a Julian date represented by a number. The `outside_range` argument determines what to do if no data is available for `date`:

  * `:warn`: The last valid value is returned and a warning will be displayed.
  * `:nothing`: The last valid value is returned.
  * `:error`: An `OutOfRangeError` is thrown.
