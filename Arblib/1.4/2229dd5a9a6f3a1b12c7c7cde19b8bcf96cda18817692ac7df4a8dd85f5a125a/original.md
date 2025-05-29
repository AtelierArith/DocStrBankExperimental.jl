```
midpoint([T, ] z::AcbOrRef)
```

Returns the midpoint of `z` as a `Complex{Arf}`. If `T` is given and equal to `Arf` or `Arb`, convert to `Complex{T}`. If `T` is equal to `Acf` or `Acb` then convert to that.

!!! note "Default type"
    For compatability reasons this functions returns `Complex{Arf}` if `T` is omitted. In a future version the default might change to `Acf`.

