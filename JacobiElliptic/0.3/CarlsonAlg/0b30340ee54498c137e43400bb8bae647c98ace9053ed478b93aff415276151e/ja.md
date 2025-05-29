```
am(u::Real, m::Real, [tol::Real=eps(Float64)])
```

振幅 φ を返します。ここで、u = F(φ | m)

`√(tol) ≤ m ≤ 1 - √(tol)` の場合、収束するランドン列が使用されます。
