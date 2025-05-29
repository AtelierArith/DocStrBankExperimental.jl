```
struct Orthotope{D,T} <: AbstractDomain{D,T}
```

Axes-aligned Orthotope in `D` dimensions, with element type `T`, given by two points `low_corner` and `high_corner`. Note that, we must have `low_corner .≤ high_corner`.

## Fields:

  * `corners::SVector{2,SVector{D,T}}`: `corners[1]` = the low corner and `corners[2]` = the  ]high corner.

## Invariants (**not** check at construction):

  * `corners[1] .≤ corners[2]`

## Constructors:

  * `Orthotope(low_corner, high_corner)`
  * `Orthotope{T}(low_corner, high_corner)`
  * `Orthotope(corners::SVector{2,SVector{D,T}})`
