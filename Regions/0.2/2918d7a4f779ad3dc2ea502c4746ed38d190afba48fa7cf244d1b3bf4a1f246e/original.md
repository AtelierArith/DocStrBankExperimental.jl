```
Run
```

A run is a set of consecutive coordinates within a row (possibly partial) of a  region. It consists of a discrete row coordinate (of type Signed) and a range  of discrete column coordinates (of type UnitRange{Int64}).

Runs within a region specify a sort order: one run is smaller than the other if it starts before the other run modeling the coordinates from left to right and top to  bottom.
