```
update_all_bounds!(data; v_min, v_max, pg_min, pg_max, qg_min, qg_max, pd_min, pd_max, qd_min, qd_max)
```

Function that combines `update_voltage_bounds!`, `update_generator_bounds!` and `update_load_bounds!` and assigns bounds to all bus voltages and load and generator power.
