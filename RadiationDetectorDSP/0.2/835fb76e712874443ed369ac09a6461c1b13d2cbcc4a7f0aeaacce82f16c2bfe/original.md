```
charge_trapflt!(samples::AbstractVector{<:RealOrSIMD{<:AbstractFloat}}, navg::Integer, ngap::Integer)
```

Apply a trapezoidal FIR filter to a charge signal in `samples`.
