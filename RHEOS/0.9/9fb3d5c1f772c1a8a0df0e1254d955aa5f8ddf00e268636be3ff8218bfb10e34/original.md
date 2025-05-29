```
cutting(self::RheoTimeData, time_on::Real, time_off::Real)
```

Remove the data outside a specified time interval.

By specifing a time interval (`time_on`, `time_off`), a new `RheoTimeData` is returned without the data lying outside time interval.
