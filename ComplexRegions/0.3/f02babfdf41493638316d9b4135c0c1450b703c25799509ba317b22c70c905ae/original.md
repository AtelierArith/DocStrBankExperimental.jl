```
isleft(z, R::Ray)
```

Determine whether the number `z` lies "to the left" of ray `R`. This means that the angle it makes with `tangent(R)` is in the interval (0,π).

Note that `isleft` and `isright` are *not* logical opposites; a point on the (extended) ray should give `false` in both cases.
