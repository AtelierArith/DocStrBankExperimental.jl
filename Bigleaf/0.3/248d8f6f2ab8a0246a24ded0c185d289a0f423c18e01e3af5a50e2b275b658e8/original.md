```
set_datetime_ydh!(df, timezone = tz"UTC+0"; 
    year = df.year, doy = df.doy, hour = df.hour)
```

Update column DateTime column datetime according to year, dayOfYear, and fractional hour.

# Value

`df` with updated or added column `:datetime` moved to the first position.
