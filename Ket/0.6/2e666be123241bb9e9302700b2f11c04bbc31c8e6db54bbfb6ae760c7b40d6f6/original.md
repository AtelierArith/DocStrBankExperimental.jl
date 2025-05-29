```
cleanup!(M::AbstractArray{T}; tol = Base.rtoldefault(real(T)))
```

Zeroes out real or imaginary parts of `M` that are smaller than `tol`.
