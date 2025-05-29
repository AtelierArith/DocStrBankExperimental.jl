```
System
```

The abstract type for representing the whole power system including topology, static components and their attributes, and time series data.

Topology: `Dictionaries` linking generators, loads, and bids (if present) to buses. System wide static components and grid matrices: zones, buses, generators, branches, LODF and PTDF. Time series data: all the time series associated with generators, loads and bids.  All stored as `KeyedArray`s of `ids x datetimes`.
