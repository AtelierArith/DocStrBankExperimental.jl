```
findmin(C::ClimGrid; skipnan::Bool=false)
```

Return the minimum element of ClimGrid C and its index. If there are multiple minimal elements, then the first one will be returned. If any data element is NaN, this element is returned. The result is in line with min. As climate data can often have NaN values (irregular polygons, missing weather data), the option to skip NaNs is provided as a keyword argument.
