```
isclose(a::Run, b::Run, x::Integer, y::Integer)
isclose(a::Run, b::Run, d::Integer)
isclose(x::Run, y::Run, distance::Vector[Int64])
```

Test if two runs are close.

If distance == 0 this is the same as isoverlapping(). If distance == 1 this is the same as istouching(). If distance > 1 this is testing of closeness.
