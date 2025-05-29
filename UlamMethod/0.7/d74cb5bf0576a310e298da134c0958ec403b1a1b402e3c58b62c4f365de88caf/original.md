```
struct HexagonBinner{M, CRS}
```

Bin a two dimensional `Polygon` with a covering of regular hexagons. 

The final number of bins may be slightly different than the number requested.

### Fields

  * `boundary`: A [`Boundary`](@ref) object.
  * `bins`: A [`Bins`](@ref) object.
  * `idx2pos`: A vector such that `idx2pos[i]` gives the position (in bins) of the bin initially (before removing dataless and disconnected bins) labelled `i`. `idx2pos[i] == nothing` if this bin was removed.

### Constructor

```
HexagonBinner(nbins, boundary; hardclip = true)
```
