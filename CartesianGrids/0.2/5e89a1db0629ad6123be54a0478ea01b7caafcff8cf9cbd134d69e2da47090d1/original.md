```
diff!(out:ScalarGridData,in::ScalarGridData) -> ScalarGridData
```

Return the 1-d central finite difference of scalar grid data `in` in scalar grid data `out`. Either `in` or `out` must be edge component data and the other must be node data. The direction of differencing is determined by the relationship of `in` and `out`. For example, if `in` is dual nodes (cell by cell) and `out` is primal x-edge components (cell by edge), then the differencing takes place in the y direction, since they are different types in this direction.
