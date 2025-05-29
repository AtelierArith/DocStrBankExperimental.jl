```
make_lonlat_mask(var;
                 set_to_val = nothing,
                 true_val = NaN,
                 false_val = 1.0)
```

Return a masking function that takes in a `OutputVar` and mask the data using `var.data`.

The parameter `set_to_val` is a function that takes in an element of `var.data` and return `true` or `false`. If `set_to_nan` returns `true`, then the value will be `true_val` in the mask and if `set_to_nan` returns `false`, then the value will be `false_val` in the mask.

If `set_to_nan` is `nothing`, then no transformation is done and `var.data` is used. This is helpful if `var.data` is already an array of NaNs and ones or an array of zeros and ones.
