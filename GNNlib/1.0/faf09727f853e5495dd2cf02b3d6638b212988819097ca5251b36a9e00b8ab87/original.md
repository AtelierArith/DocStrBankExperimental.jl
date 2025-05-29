```
e_mul_xj(xi, xj, e) = reshape(e, (...)) .* xj
```

Reshape `e` into a broadcast compatible shape with `xj` (by prepending singleton dimensions) then perform broadcasted multiplication.
