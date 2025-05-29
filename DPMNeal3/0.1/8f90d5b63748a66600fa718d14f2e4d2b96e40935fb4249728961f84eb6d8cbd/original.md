```
update_suffstats!(m::AbstractDPM, data, i::Int, k::Int, l::Int)
```

Update the sufficient statistics in `m` after the `i`th cluster label changes  from `k` to `l`, given the dataset `data`.
