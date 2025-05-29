```
get_orientation(p, q, r; rtol=1e-4, atol=1e-6)
```

Determine orientation of three points. 

Colinear is returned if `cross(pq, qr) <= tol`, where `tol` is the 

  * `atol` if either magnitude is less than `atol`.
  * `rtol * |pq||qr|` otherwise, where `cross(pq, qr) ≈ |pq||qr|θ` for small `θ`.

Clockwise is returned if `cross(pq, qr)` is positive, else counter-clockwise.
