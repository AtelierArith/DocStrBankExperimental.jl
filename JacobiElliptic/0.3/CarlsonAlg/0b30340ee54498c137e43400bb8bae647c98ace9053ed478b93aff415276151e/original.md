```
am(u::Real, m::Real, [tol::Real=eps(Float64)])
```

Returns amplitude, φ, such that u = F(φ | m)

Landen sequence with convergence to `tol` used if `√(tol) ≤ m ≤ 1 - √(tol)`
