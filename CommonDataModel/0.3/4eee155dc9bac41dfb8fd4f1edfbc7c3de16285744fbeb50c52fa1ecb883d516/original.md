```
b = bounds(ncvar::NCDatasets.CFVariable)
```

Return the CFVariable corresponding to the `bounds` attribute of the variable `ncvar`. The time units and calendar from the `ncvar` are used but not the attributes controling the packing of data `scale_factor`, `add_offset` and `_FillValue`.
