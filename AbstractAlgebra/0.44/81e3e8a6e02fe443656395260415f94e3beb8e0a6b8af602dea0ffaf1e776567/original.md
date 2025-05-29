```
divides(f::T, g::T) where T <: RingElem
```

Return a pair, `flag, q`, where `flag` is set to `true` if $g$ divides $f$, in which case `q` is set to the quotient, or `flag` is set to `false` and `q` is undefined.
