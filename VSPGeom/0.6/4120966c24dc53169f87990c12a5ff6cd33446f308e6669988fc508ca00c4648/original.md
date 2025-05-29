```
degenGeomSize(degenGeom::DataFrame)
```

Get size of the 2d mesh data structure that describes the degenerate geometry. This is different from the DataFrame size obtained using `size(degenGeom)` which is the number of variables and total number of points in the DataFrame.

**Arguments**

  * `degenGeom::DataFrame`: One of the degenGeom inside the [`VSPComponent`](@ref) object

**Returns**

  * `nx::Int`: Usually represents the number of cross-sections, referred to as Xsecs in OpenVSP
  * `ny::Int`: Usually represents the number of points in each cross-section in OpenVSP
