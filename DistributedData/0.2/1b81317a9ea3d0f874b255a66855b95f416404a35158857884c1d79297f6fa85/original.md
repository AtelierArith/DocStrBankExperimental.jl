```
dscale(dInfo::Dinfo, columns::Vector{Int})
```

Scale the columns in the dataset to have mean 0 and sdev 1.

Prevents creation of NaNs by avoiding division by zero sdevs.
