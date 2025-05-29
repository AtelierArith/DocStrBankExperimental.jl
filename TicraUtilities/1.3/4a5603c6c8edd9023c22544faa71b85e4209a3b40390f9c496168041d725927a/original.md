```
get_powerms(s::SPHQPartition)
```

Return the offset vector `powerms`. The vector has axes `(0:mmax)` (i.e. it can be indexed  with integers `m` ranging from `0` to `mmax`) and its `m`th element contains the total power (one-half the sum of the magnitude squared) of all modes with `±m` as the `m` index.
