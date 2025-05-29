```
struct RectangleBinner{M, CRS}
```

Bin a two dimensional `Polygon` with a tight covering of rectangles. The rectangles are chosen to be as close as possible to squares and so the final number of bins may be slightly different than the number requested.

### Fields

  * `boundary`: A [`Boundary`](@ref) object.
  * `bins`: A [`Bins`](@ref) object.
  * `idx2pos`: A vector such that `idx2pos[i]` gives the position (in bins) of the bin initially (before removing dataless and disconnected bins) labelled `i`. `idx2pos[i] == nothing` if this bin was removed.

### Constructor

```
RectangleBinner(nbins, boundary; hardclip = true)
```

`nbins` can be:

  * An `Integer`, in which case a `RectangleBinner` will be constructed attempting to distribute boxes proportionally across `x` and y`such that the total number of boxes is as close as possible to`nbins`.
  * An `NTuple{2, Integer}`, in which case dimension `i` receives `nbins[i]` bins.
  * An `NTuple{2, AbstractVector}`, in which case `nbins[i]` defines the edges of the bins in dimension `i`.
