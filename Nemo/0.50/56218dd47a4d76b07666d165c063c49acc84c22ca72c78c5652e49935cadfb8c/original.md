```
divisor_lenstra(n::ZZRingElem, r::ZZRingElem, m::ZZRingElem)
```

If $n$ has a factor which lies in the residue class $r (\mod m)$ for $0 < r < m < n$, this function returns such a factor. Otherwise it returns $0$. This is only efficient if $m$ is at least the cube root of $n$. We require gcd$(r, m) = 1$ and this condition is not checked.
