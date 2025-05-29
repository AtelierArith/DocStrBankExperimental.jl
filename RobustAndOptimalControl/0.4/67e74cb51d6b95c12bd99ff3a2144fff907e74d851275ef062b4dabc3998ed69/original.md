```
extended_controller(K::AbstractStateSpace)
```

Takes a controller and returns an `ExtendedStateSpace` version which has augmented input `[r; y]` and output `y` (`z` output is 0-dim).
