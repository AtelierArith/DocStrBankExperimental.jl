```
induce_crt(L::Vector{MatElem}, c::crt_env{ZZRingElem}) -> ZZMatrix
```

Given matrices $L[i]$ and a `crt\_env`, apply the `crt` function to each coefficient resulting in a matrix $M = L[i] \bmod p[i]$.
