```
isclose(::UnitRange{Int64}x, ::UnitRange{Int64}y, distance::Integer)
```

Test if two ranges are close.

If distance == 0 this is the same as isoverlapping(). If distance == 1 this is the same as istouching(). If distance > 1 this is testing of closeness.
