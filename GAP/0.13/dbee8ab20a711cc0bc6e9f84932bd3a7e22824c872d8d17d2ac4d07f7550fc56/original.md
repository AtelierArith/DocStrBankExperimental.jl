```
GapInt
```

Any GAP integer object is represented in Julia as either a `GapObj` (if it is a "large" integer) or as an `Int` (if it is a "small" integer). This type union can be used to express this conveniently, e.g. when one wants to help type stability.

Note that also GAP's `infinity` and `-infinity` fit under this type (as do many other objects which are not numbers).
