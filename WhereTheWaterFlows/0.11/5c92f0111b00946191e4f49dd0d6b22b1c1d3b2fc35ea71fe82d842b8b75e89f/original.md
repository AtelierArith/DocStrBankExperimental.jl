```
prune_catchments(catchments, minsize; val=0)
```

Sets all catchments which are smaller than minsize to `val` (=0). Catchments with number <1 are ignored.

Note that, as the catchments are re-numbered, the number will not correspond to the sinks and pits anymore.
