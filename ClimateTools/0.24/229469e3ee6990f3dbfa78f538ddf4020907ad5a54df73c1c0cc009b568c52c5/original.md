```
findmax(C::ClimGrid; skipnan::Bool=false)
```

Return the maximum element of ClimGrid C and its index. If there are multiple maximal elements, then the first one will be returned. If any data element is NaN, this element is returned. The result is in line with max. As climate data can often have NaN values (irregular polygons, missing weather data), the option to skip NaNs is provided as a keyword argument.
