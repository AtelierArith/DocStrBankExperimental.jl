```
PVTKData
```

Convenience type to hold information about available data arrays for cells or points.

Supports a collectible/dictionary-like syntax, e.g., `keys(pvtk_data)` to show available data arrays or `pvtk_data["varname"]` to retrieve the `VTKDataArray` for variable `varname`.
