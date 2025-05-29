```
dcca(x,y; box_start = 3, box_stop = div(length(x),10), nb_pts = 30)
```

Performs the DCCA analysis of `x` and `y`. The default analysis starts with a window size of 3 up to one tenth of the total length of `x` for statistical reasons.

returns the dcca coefficients.
