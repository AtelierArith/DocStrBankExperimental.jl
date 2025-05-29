```
getringinfo!(resol::Resolution, ring, ringinfo::RingInfo; full=true) :: RingInfo
```

Fill the RingInfo structure with information about the specified ring. If `full` is `false`, the field `colatitude_rad` (the most expensive in terms of computation) is set to `NaN`.
