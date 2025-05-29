```
getyp(date; outside_range=:warn)
```

Get the y-coordinate of Earth's north pole w.r.t. the CIO for a certain `date` in arcseconds.

`date` can either be a `DateTime` object or a Julian date represented by a number. The `outside_range` argument determines what to do if no data is available for `date`:

  * `:warn`: The last valid value is returned and a warning will be displayed.
  * `:nothing`: The last valid value is returned.
  * `:error`: An `OutOfRangeError` is thrown.
