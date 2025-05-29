```
 slice1d(bd, var, icut::Int=1, dir::Int=2)
```

Return view of variable `var` in `bd` along 1D slice. `icut` is the index along axis `dir`. `dir == 1` means align with the 2nd (y) axis, `dir == 2` means align with the 1st (x) axis.
