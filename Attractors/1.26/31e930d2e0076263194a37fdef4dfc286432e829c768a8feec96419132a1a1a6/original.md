```
continuation_series(continuation_info, fillval = NaN)
```

Transform a continuation quantity (a vector of dictionaries, each dictionary mapping attractor IDs to values of same type as `fillval`) to a dictionary of vectors where the `k` dictionary entry is the series of the continuation quantity corresponding to attractor with ID `k`. `fillval` denotes the value to assign in the series if the attractor with ID `k` does not exist at this particular series index.
