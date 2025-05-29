```
isright(z, R::Ray)
```

Determine whether the number `z` lies "to the right" of ray `R`. This means that the angle it makes with `tangent(R)` is in the interval (-π,0).

Note that `isleft` and `isright` are *not* logical opposites; a point on the (extended) ray should give `false` in both cases.
