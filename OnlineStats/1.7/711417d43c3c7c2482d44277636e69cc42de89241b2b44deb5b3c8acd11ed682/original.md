```
ExpandingHist(nbins)
```

An adaptive histogram where the bin edges keep doubling in size in order to contain every observation. `nbins` must be an even number.  Bins are left-closed and the rightmost bin is closed, e.g.

  * `[a, b)`, `[b, c)`, `[c, d]`

# Example

```
o = fit!(ExpandingHist(200), randn(10^6))

using Plots
plot(o)
```

# Details

How `ExpandingHist` works is best understood through example.  Suppose we start with a histogram of edges/counts as follows:

```
|1|2|5|3|2|
```

  * Now we observe a data point that is not contained in the bin edges:

```
|1|2|5|3|2|       *
```

  * In order to contain the point, the range of the edges doubles in the direction of the new data point and adjacent bins merge their counts:

```
|1|2|5|3|2|       *
 \ / \ / \ /      ↓
  ↓   ↓   ↓       ↓
| 3 | 8 | 2 | 0 | 1 |
```

  * Note that multiple iterations of bin-doubling may occur until the new point is contained by the bin edges.
