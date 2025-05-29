```
hold(flag::Bool)
```

Set the hold flag for combining multiple plots.

`hold(true)` prevents clearing previous plots, so that next plots will be drawn on top of the previous one until `hold(false)` is called.

Use the keyword argument `hold=<true/false>` in plotting functions, to set the hold flag during the creation of plots.
