```
get_ind(xyz::XYZ;
        ind    = trues(xyz.traj.N),
        lines  = (),
        tt_lim = (),
        splits = (1))
```

Get BitVector of indices for further analysis from specified indices (subset), lines, and/or time range. Any or all of these may be used. Defaults to use all indices, lines, and times.

**Arguments:**

  * `xyz`:    `XYZ` flight data struct
  * `ind`:    (optional) selected data indices
  * `lines`:  (optional) selected line number(s)
  * `tt_lim`: (optional) end time limit or length-`2` start & end time limits (inclusive) [s]
  * `splits`: (optional) data splits, must sum to 1

**Returns:**

  * `ind`: BitVector (or tuple of BitVector) of selected data indices
