```
FritschCarlsonMonotonicInterpolation
```

Monotonic interpolation based on [Fritsch & Carlson (1980), "Monotone Piecewise Cubic Interpolation", doi:10.1137/0717021](@cite Fritsch1980).

Tangents are first initialized, then adjusted if they are not monotonic can overshoot for non-monotonic data
