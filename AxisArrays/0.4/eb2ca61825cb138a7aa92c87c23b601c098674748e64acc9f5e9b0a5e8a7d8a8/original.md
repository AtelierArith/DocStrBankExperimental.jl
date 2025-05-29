```
merge(As::AxisArray...)
```

Combines AxisArrays with matching axis names into a single AxisArray spanning all of the axis values of the inputs. If a coordinate is defined in more than ones of the inputs, it takes its value from last input in which it appears. If a coordinate in the output array is not defined in any of the input arrays, it takes the value of the optional `fillvalue` keyword argument (default zero).
