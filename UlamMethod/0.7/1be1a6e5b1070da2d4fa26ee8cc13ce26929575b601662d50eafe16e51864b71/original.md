```
struct LineBinner{M, CRS}
```

Bin a one dimensional `Segment` (line segement) with `nbins` equally-spaced bins.

### Fields

  * `boundary`: A [`Boundary`](@ref) object.
  * `bins`: A [`Bins`](@ref) object.
  * `idx2pos`: A vector such that `idx2pos[i]` gives the position (in bins) of the bin initially (before removing dataless and disconnected bins) labelled `i`. `idx2pos[i] == nothing` if this bin was removed.

### Constructor

```
LineBinner(nbins, boundary; hardclip = true)
```
