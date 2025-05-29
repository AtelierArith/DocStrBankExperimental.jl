```
Bins(f, bins; labels, pad)
Bins(bins; labels, pad)
```

Specify bins to reduce groups after applying function `f`.

  * `f`: a grouping function of the lookup values, by default `identity`.
  * `bins`:

      * an `Integer` will divide the group values into equally spaced sections.
      * an `AbstractArray` of values will be treated as exact   matches for the return value of `f`. For example, `1:3` will create 3 bins - 1, 2, 3.
      * an `AbstractArray` of `IntervalSets.Interval` can be used to   explicitly define the intervals. Overlapping intervals have undefined behaviour.

## Keywords

  * `pad`: fraction of the total interval to pad at each end when `Bins` contains an  `Integer`. This avoids losing the edge values. Note this is a messy solution -  it will often be prefereble to manually specify a `Vector` of chosen `Interval`s  rather than relying on passing an `Integer` and `pad`.
  * `labels`: a list of descriptive labels for the bins. The labels need to have the same length as `bins`.

When the return value of `f` is a tuple, binning is applied to the *last* value of the tuples.
