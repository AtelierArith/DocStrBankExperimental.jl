```
get_orientation(p, q, r; rtol=1e-4, atol=1e-6)
```

三点の向きを決定します。

`cross(pq, qr) <= tol` の場合、 colinear が返されます。ここで `tol` は 

  * いずれかの大きさが `atol` より小さい場合は `atol`。
  * それ以外の場合は `rtol * |pq||qr|` であり、ここで `cross(pq, qr) ≈ |pq||qr|θ` は小さい `θ` に対して成り立ちます。

`cross(pq, qr)` が正の場合は時計回りが返され、それ以外の場合は反時計回りが返されます。
