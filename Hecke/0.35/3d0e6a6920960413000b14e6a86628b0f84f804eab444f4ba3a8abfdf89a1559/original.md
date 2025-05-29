```
PrimesSet(f::Integer, t::Integer) -> PrimesSet
PrimesSet(f::ZZRingElem, t::ZZRingElem) -> PrimesSet
```

Returns an iterable object $S$ representing the prime numbers $p$ for $f \le p \le t$. If $t=-1$, then the upper bound is infinite.
