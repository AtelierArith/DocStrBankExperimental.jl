```
inventory = co2_inventory(model, ws, states, t; cells = missing, co2_name = "CO2")
inventory = co2_inventory(model, result::ReservoirSimResult; cells = missing)
```

Compute CO2 inventory for each step for a given `model`, well results `ws` and reporting times t. If provided, the keyword argument `cells` will compute inventory inside the region defined by the cells, and let any additional CO2 be categorized as "outside region".

The inventory will be a Vector of Dicts where each entry contains a breakdown of the status of the CO2 at that time, including residual and dissolution trapping.
