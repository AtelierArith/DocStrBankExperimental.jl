```
IncrementBinner([::Type{T}; blocksize = 64])
IncrementBinner(zero_element::T[; blocksize = 64])
```

Creates an `IncrementBinner` from a `zero_element` numeric type `T`.

Values pushed to an `IncrementBinner` are averaged in stages. For the first `blocksize` values pushed no averaging happens. After that `2blocksize` elements are averaged 2 at a time, then `4blocksize` element 4 at a time, etc. This means values pushed become progressively more compressed and smoothed.
