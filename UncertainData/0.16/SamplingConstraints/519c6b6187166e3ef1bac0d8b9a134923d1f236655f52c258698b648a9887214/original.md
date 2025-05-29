```
sequence_exists(udata::AbstractUncertainValueDataset, c::StrictlyDecreasing{StartToEnd})
```

Does a strictly decreasing sequence through the dataset exist? I.e,  check that a strictly  decreasing sequence can be found after first  constraining each distribution to the provided quantile range (this  is necessary because some distributions may have infinite support).
