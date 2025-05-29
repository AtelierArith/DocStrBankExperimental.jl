```julia
negative_slope_currently(a; i, back) -> Any

```

Return true if a is currently sloping down.  In other words, `a[i] < a[i+back]`.
