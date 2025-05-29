```
modify_model!(mod::FuelPrice, config, data, model)
```

  * Make `data[:fuel_markets]` to keep track of each of the fuel markets
  * Add variable `fuel_sold[fuel_price_idx,  yr_idx, hr_idx]`: total fuel sold at each price step for each time interval
  * Add expression `fuel_used[fuel_market_idx, yr_idx, hr_idx]`: total fuel used by generators for each market region for each time interval
  * Add expression `fuel_price_obj[fuel_market_idx, yr_idx, hr_idx]`: total cost of the fuel, added to the objective.
  * Add constraint `cons_fuel_sold[fuel_price_idx, yr_idx]`: constrain the total `fuel_sold` in each year to be ≤ yearly quantity
  * Add constraint `cons_fuel_bal[fuel_market_idx, yr_idx, hr_idx]`: constrain the amount of fuel sold in each market region to equal the amount of fuel used in each market region.

`fuel_sold` and `fuel_used` will be scaled down using the fp_scalar to reduce the difference in size between the variables used together in these constraints.  This prevents issues with shadow prices which can sometimes be rounded to 0 when the objective scalar is high. 
