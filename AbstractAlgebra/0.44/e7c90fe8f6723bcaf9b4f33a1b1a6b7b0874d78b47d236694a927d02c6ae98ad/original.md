```
gcdinv(f::T, g::T) where T <: RingElem
```

Return a tuple `d, s` such that $d = gcd(f, g)$ and $s = (f/d)^{-1} \pmod{g/d}$. Note that $d = 1$ iff $f$ is invertible modulo $g$, in which case $s = f^{-1} \pmod{g}$.
