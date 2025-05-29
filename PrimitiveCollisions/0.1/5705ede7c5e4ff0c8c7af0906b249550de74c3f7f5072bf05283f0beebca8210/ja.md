```julia
struct Rect{R<:Real} <: AbstractPolygon{2}
```

2次元の長方形で、両方の次元においてその半分の範囲（`half_ext`）を格納します。
