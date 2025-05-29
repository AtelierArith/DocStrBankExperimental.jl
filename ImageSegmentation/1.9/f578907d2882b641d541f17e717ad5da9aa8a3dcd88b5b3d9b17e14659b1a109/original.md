```
remove_segment!(seg, label, diff_fn)
```

In place removal of the segment having label `label`, replacing it with the neighboring segment having least `diff_fn` value.

```
d = diff_fn(rem_label, neigh_label)
```

A difference measure between label to be removed and its neighbors. `isless` must be defined for objects of the type of `d`.

# Examples

```julia
    # This removes the label `l` and replaces it with the label of
    # neighbor having maximum pixel count.
    julia> remove_segment!(seg, l, (i,j)->(-seg.segment_pixel_count[j]))

    # This removes the label `l` and replaces it with the label of
    # neighbor having the least value of euclidian metric.
    julia> remove_segment!(seg, l, (i,j)->sum(abs2, seg.segment_means[i]-seg.segment_means[j]))
```
