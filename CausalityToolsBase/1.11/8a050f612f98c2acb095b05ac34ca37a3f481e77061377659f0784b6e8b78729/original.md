```
customembed(pts, positions::Positions, lags::Lags)
```

Do custom state space reconstructions with `customembed(pts, positions::Positions, lags::Lags)`.  This function acts almost as `DynamicalSystems.reconstruct`, but allows for more flexibility in  the ordering of dynamical variables and allows for negative lags. The `positions` variable  indicates which dynamical variables are mapped to which variables in the final  reconstruction, while `lags` indicates the lags for each of the embedding variables. 

Example: `customembed([rand(3) for i = 1:50], Positions(1, 2, 1, 3), Lags(0, 0, 1, -2)`  gives a 4-dimensional embedding with state vectors `(x1(t), x2(t), x1(t + 1), x3(t - 2))`. 

Note: `customembed` expects an array of *state vectors*, i.e. `pts[k]` must refer to the  `k`th point of the dataset, not the `k`th dynamical variable/column.*. To embed a vector of  time series, load `DynamicalSystems` and wrap the time series in a `Dataset` first, e.g. if  `x = rand(100); y = rand(100)` are two time series, then  `customembed(Dataset(x, y), Positions(1, 2, 2), Lags(0, 0, 1)` will create the embedding with  state vectors `(x(t), y(t), y(t + 1))`.

Pre-embedded points may be wrapped in a `CustomReconstruction` instance by simply calling  `customembed(preembedded_pts)` without any position/lag instructions.
