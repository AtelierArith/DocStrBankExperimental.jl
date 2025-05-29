```
conformables{T, S, O1, O2}(map1::HealpixMap{T, O1, AA1},
                           map2::HealpixMap{S, O2, AA2}) -> Bool
conformables{T, S, O1, O2}(map1::PolarizedHealpixMap{T, O1, AA1},
                           map2::PolarizedHealpixMap{S, O2, AA2}) -> Bool
```

Determine if two Healpix maps are "conformables", i.e., if their shape and ordering are the same. The array types `AA1` and `AA2` are not considered in testing conformability.
