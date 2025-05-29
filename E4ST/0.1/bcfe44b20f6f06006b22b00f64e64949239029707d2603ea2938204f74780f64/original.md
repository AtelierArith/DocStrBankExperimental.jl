```
parse_comparison(s) -> comp
```

Parses the string, `s` for a comparison with which to filter a table.

Possible examples of strings `s` to parse:

  * `"nation=>narnia"` - All rows for which row.nation=="narnia"
  * `"bus_idx=>5"` - All rows for which row.bus_idx==5
  * `"year_on=>(y2002,y2030)"` - All rows for which `row.year_on` is between 2002 and 2030, inclusive.
  * `"emis_co2=>(0.0,4.99)"` - All rows for which `row.emis_co2` is between 0.0 and 4.99, inclusive. (Works for integers and negatives too)
  * `"emis_co2=> >(0)"` - All rows for which `row.emis_co2` is greater than 0 (Works for integers and negatives too)
  * `"year_on=> >(y2002)` - All rows for which `row.year_on` is greater than "y2002" (works for fractional years too, such as "y2002.4")
  * `"genfuel=>[ng, wind, solar]"` - All rows for which `row.genfuel` is "ng", "wind", or "solar".  Works for Ints and Floats too.
  * `"genfuel=>![ng, coal, biomass]"` - All rows for which `row.genfuel` is not "ng", "coal", or "biomass".  Works for Ints and Floats too.
