```
add_arrows!(plt::PlotlyJS.SyncPlot, origin::Vector{<:Real}, dir::Vector{<:Real}, len::Real=1.0, color::String=""; opc::Real=1, endpoint::Bool=true, asize::Real=len)

Creates a 3D arrow starting from a point and pointing in a given direction.

# Arguments
- `plt::PlotlyJS.SyncPlot`: The plot to which the axes will be added.
- `origin::Vector{<:Real}`: The starting point of the arrow.
- `dir::Vector{<:Real}`: The direction vector of the arrow.
- `len::Real`: length of the arrow
- `color::String`: The color of the arrow.

# Keywords
- `opc`: The opacity of the arrow. Default is 1.
- `asize` Size factor of the arrow cone. Default is `len`.
```
