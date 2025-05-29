```
isright(z,S::Segment)
```

Determine whether the number `z` lies "to the right" of segment `S`. This means that the angle it makes with `tangent(S)` is in the interval (-π,0).

Note that `isleft` and `isright` are *not* logical opposites; a point on the (extended) segment should give `false` in both cases.
