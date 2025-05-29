```
threshold!(px, metric; threshold)
```

Remove vertices from `px::Parcellation` where `metric` (such as an edgemap) exceeds a maximum value, defined as the `threshold` quantile of values from `metric`. If any parcels are separated or disconnected in this process, then split their new connected components that emerged into new parcels.

Returns the number of high vertices removed in this process.
