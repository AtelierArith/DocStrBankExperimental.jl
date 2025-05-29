```
source(anchorPnt::Point = Point())
```

return a tuple that describe the source (`anchorPnt`, `SrcRadius`, `SrcLength`) according to  the input from the `console`.

  * `anchorPnt` : the source anchoring point. if it is missing the user is prompt   to input it via the `console`.
  * `SrcRadius` : source radius.
  * `SrcLength` : source length.

!!! warning
    if source type set to point source, both `SrcRadius` and `SrcLength` are set to zero.  for more information **see also:** [`typeofSrc()`](@ref) and [`typeofSrc(x::Int)`](@ref).

