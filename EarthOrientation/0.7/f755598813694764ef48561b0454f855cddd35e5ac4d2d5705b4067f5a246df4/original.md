```
precession_nutation80(date; outside_range=:warn)
```

Get the ecliptic corrections for a certain `date` in milliarcseconds.

`date` can either be a `DateTime` object or a Julian date represented by a number. The `outside_range` argument determines what to do if no data is available for `date`:

  * `:warn`: The last valid value is returned and a warning will be displayed.
  * `:nothing`: The last valid value is returned.
  * `:error`: An `OutOfRangeError` is thrown.
