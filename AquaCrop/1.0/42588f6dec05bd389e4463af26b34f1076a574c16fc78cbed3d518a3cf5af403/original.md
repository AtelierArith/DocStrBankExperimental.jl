```
canopycover(cropfield::AquaCropField; actual=true)
```

Returns the canopy cover of the `cropfield` in percentage of terrain covered.

If `actual=true`, returns the canopy cover just before harvesting, otherwise returns the canopy cover just after harvesting

The harvesting is done at the end of the day.
