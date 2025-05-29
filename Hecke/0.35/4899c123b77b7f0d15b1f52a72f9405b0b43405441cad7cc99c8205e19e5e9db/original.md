```
induce_crt(L::Vector{PolyRingElem}, c::crt_env{ZZRingElem}) -> ZZPolyRingElem
```

Given ZZRingElem_poly polynomials $L[i]$ and a `crt\_env`, apply the `crt` function to each coefficient resulting in a polynomial $f = L[i] \bmod p[i]$.
