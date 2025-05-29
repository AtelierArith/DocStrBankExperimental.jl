```
modify_results!(mod::FuelPrice, config, data)
```

  * Calculate the clearing price for each market region for each fuel type.

      * Equal to the shadow price of `cons_fuel_sold` for the cheapest fuel price step in the region plus the cheapest fuel price
      * Add it to `fuel_markets.clearing_price` column
      * Update `gen.fuel_price` column to use the clearing price (multiplied by the `heat_rate` column)
