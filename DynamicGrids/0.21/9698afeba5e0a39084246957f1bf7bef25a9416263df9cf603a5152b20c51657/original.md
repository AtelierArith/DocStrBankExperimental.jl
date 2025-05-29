```
RunAt(rules...)
RunAt(rules::Tuple)
```

`RunAt`s allow running a `Rule` or multiple `Rule`s at a lower frequeny than the main simulation, using a `range` matching the main `tspan` but with a larger span, or specific events - by using a vector of arbitrary times in `tspan`.
