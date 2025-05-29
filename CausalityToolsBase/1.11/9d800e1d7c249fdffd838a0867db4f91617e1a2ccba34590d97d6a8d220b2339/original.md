```
customembed(pts, positions::Positions, lags::Lags)
```

Creates a custom embedding from a set of points (`pts`),  where the i-th embedding column/variable is constructed by lagging the `positions[i]`-th variable/column of `pts` by  a lag of `lags[i]`. 

*Note: `pts[k]` must refer to the `k`th point of the dataset, not the `k`th dynamical variable/column.*
