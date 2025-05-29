```
update_voltage_bounds!(data; v_min, v_max)
```

Function that allows to automatically set upper (v*max) and lower (v*min) voltage bounds for all buses. It assumes that all bus terminals have the same bounds and that there are at most four active terminals.
