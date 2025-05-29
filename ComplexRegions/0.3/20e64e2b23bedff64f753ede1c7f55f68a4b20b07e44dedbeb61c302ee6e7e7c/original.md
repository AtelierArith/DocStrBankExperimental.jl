```
isright(z, L::Line)
```

Determine whether the number `z` lies "to the right" of line `L`. This means that the angle it makes with `tangent(L)` is in the interval (-π,0).

Note that `isleft` and `isright` are *not* logical opposites; a point on the curve should give `false` in both cases.
