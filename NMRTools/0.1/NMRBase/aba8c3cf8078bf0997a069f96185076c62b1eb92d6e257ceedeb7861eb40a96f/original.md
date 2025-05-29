```
add_offset!(data::NMRData, dim_ref, offset)
```

Add an offset to a frequency dimension in an NMRData object. The dimension can be specified as a numerical index or an object like `F1Dim`. The metadata is copied using `replacedimension`, and an entry is added or updated in the dimension metadata to record the offset change.
