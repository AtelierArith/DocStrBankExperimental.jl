```
modify_setup_data!(mod::FuelPrice, config, data)
```

Zero out the `fuel_price` column of the `gen` table, as it will get overwritten later by this Modification.  This is to avoid double-counting the fuel cost.
