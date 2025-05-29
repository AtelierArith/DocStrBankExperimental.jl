```
reinit!(cv::CellValues, cell::AbstractCell, x::AbstractVector)
reinit!(cv::CellValues, x::AbstractVector)
reinit!(fv::FacetValues, cell::AbstractCell, x::AbstractVector, facet::Int)
reinit!(fv::FacetValues, x::AbstractVector, function_gradient::Int)
```

Update the `CellValues`/`FacetValues` object for a cell or facet with cell coordinates `x`. The derivatives of the shape functions, and the new integration weights are computed. For interpolations with non-identity mappings, the current `cell` is also required.
