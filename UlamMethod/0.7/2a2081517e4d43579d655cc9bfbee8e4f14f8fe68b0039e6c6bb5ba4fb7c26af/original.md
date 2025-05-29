```
struct HyperRectangleBinner{Dim, M, CRS}
```

Bin `Dim`-dimensional (where `Dim ≥ 3`) dataset based on a tight covering of identical HyperRectangles.

The hyperrectangles are chosen to be as close as possible to hypercubes.

The `HyperRectangleBinner` does not have hard clipping functionality. However, bins with no data are  still removed in the main Ulam's method calculation.

The final number of bins may be different (larger) than the number requested.

### Fields

  * `boundary`: A [`Boundary`](@ref) object.
  * `bins`: A [`Bins`](@ref) object.
  * `idx2pos`: A vector such that `idx2pos[i]` gives the position (in bins) of the bin initially (before removing dataless and disconnected bins) labelled `i`. `idx2pos[i] == nothing` if this bin was removed.
  * `ranges`: A vector such that `ranges[i]` is the `AbstractRange` giving the gridpoints of the bins along dimension `i`.

### Constructor

```
HyperRectangleBinner(nbins, boundary)
```

`nbins` can be:

  * An `Integer`, in which case a `HyperRectangleBinner` will be constructed attempting to distribute boxes proportionally across dimensions such that the total number of boxes is as close as possible to `nbins`.
  * An `NTuple{Dim, Integer}`, in which case dimension `i` receives `nbins[i]` bins.
