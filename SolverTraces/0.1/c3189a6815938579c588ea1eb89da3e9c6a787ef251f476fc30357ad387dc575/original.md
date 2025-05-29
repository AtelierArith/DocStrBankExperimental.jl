```
LinearColorant(a, b, colors)
```

Helper structure to linearly interpolate between the possible values in `colors`, where the scalar value `a` corresponds to the first value and `b` to the last. If `colors` is a tuple of two triples, a continuous interpolation between the endpoints will be the result, whereas if it is a vector of `Crayon`s, nearest neighbour interpolation will be performed instead.
