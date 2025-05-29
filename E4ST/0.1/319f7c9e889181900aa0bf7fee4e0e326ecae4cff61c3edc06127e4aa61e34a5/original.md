```
E4ST.modify_setup_data!(pol::ITCStorage, config, data)
```

Creates a column in the gen table with the ITCStorage value in each simulation year for the qualifying generators.

ITCStorage values are calculated based on `capex_obj` so ITCStorage values only apply in `year_on` for a generator.
