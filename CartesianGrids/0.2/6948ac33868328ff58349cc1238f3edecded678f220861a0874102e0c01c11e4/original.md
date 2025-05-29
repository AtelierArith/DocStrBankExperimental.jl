```
grid_interpolate!(out:ScalarGridData,in::ScalarGridData) -> ScalarGridData
```

Return the 1-d symmetric interpolation of scalar grid data `in` onto scalar grid data `out`. Either `in` or `out` must be edge component data and the other must be node data. The direction of interpolation is determined by the relationship of `in` and `out`. For example, if `in` is dual nodes (cell by cell) and `out` is primal x-edge components (cell by edge), then the interpolation takes place in the y direction, since they are different types in this direction. (In the x direction, they are of the same type (cell), so there is no interpolation in that direction.)
