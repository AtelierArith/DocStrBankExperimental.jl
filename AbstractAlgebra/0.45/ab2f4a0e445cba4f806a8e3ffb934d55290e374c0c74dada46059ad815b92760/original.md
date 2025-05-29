```
invmod(f::T, m::T) where T <: RingElem
```

Return an inverse of $f$ modulo $m$, meaning that `isone(mod(invmod(f,m)*f,m))` returns `true`.

If such an inverse doesn't exist, a `NotInvertibleError` should be thrown.
