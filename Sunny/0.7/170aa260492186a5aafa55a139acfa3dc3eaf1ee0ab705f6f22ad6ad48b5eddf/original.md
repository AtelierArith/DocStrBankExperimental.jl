```
spin_label(sys::System, i::Int)
```

If atom `i` (referenced from the original crystal) carries a single spin-$s$ moment, then returns the half-integer label $s$. Otherwise, throws an error.
