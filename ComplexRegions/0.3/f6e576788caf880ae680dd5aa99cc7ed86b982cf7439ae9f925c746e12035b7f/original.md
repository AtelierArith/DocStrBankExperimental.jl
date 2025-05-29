```
isleft(z,S::Segment)
```

Determine whether the number `z` lies "to the left" of segment `S`. This means that the angle it makes with `tangent(S)` is in the interval (0,π).

Note that `isleft` and `isright` are *not* logical opposites; a point on the (extended) segment should give `false` in both cases.
