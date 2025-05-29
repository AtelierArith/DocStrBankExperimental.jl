```
PrimesSet(f::Integer, t::Integer, mod::Integer, val::Integer)
PrimesSet(f::ZZRingElem, t::ZZRingElem, mod::ZZRingElem, val::ZZRingElem)
```

Returns an iterable object $S$ representing the prime numbers $p$ for $f \le p \le t$ and $p\equiv val \bmod mod$ (primes in arithmetic progression).  If $t=-1$, then the upper bound is infinite.
