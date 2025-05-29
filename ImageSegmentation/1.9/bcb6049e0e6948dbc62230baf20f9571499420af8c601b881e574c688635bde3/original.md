```
new_seg = prune_segments(seg, rem_labels, diff_fn)
```

Removes all segments that have labels in `rem_labels` replacing them with their neighbouring segment having least `diff_fn`. `rem_labels` is a `Vector` of labels.

```
new_seg = prune_segments(seg, is_rem, diff_fn)
```

Removes all segments for which `is_rem` returns true replacing them with their neighbouring segment having least `diff_fn`.

```
is_rem(label) -> Bool
```

Returns true if label `label` is to be removed otherwise false.

```
d = diff_fn(rem_label, neigh_label)
```

A difference measure between label to be removed and its neighbors. `isless` must be defined for objects of the type of `d`.
