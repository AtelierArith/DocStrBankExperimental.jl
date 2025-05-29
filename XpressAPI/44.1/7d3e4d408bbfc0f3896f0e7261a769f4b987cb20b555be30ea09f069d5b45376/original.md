```
XPRS_GLOBALSPATIALBRANCHIFPREFERORIG
```

Whether spatial branchings on original variables should be preferred over branching on auxiliary variables that were introduced by the reformulation of the global solver. (integer)

Default value: `-1`

Values: -1 : Automatically determined. 0 : Always consider both original and auxiliary variables. 1 : Always prefer branching on original variables over auxiliaries. 2 : Always prefer branching on auxiliary variables over originals.
