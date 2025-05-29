```
join(As::AxisArray...)
```

Combines AxisArrays with matching axis names into a single AxisArray. Unlike `merge`, the inputs are joined along a newly created axis (optionally specified with the `newaxis` keyword argument).  The `method` keyword argument can be used to specify the join type:

`:inner` - keep only those array values at axis values common to all AxisArrays to be joined `:left` - keep only those array values at axis values present in the first AxisArray passed `:right` - keep only those array values at axis values present in the last AxisArray passed `:outer` (default) - keep all array values: create an AxisArray spanning all of the input axis values

If an array value in the output array is not defined in any of the input arrays (i.e. in the case of a left, right, or outer join), it takes the value of the optional `fillvalue` keyword argument (default zero).
