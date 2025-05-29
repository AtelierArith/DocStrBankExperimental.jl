```
clims_convex_hull!(plots)
clims_convex_hull!(plots...)
```

Set the c-axis limits for all `plots` to the smallest interval that contains all the existing c-axis limits.

If the arguments are `Subplot`s, then there is no ambiguity over the limits of a given argument. However, if they are `Plot`s, then we do the following:     * Let `n` be the minimum number of subplots across all arguments.     * For `i` in `1:n`, apply clims*convex*hull! to the all of the `i`th subplots.

This is useful to ensure that two plots are visually comparable.
