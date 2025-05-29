```
gcdx(f::T, g::T) where T <: RingElem
```

Return a triple `d, s, t` such that $d = gcd(f, g)$ and $d = sf + tg$, with $s$ loosely reduced modulo $g/d$ and $t$ loosely reduced modulo $f/d$.
