```
induce_rational_reconstruction(a::ZZPolyRingElem, M::ZZRingElem) -> QQPolyRingElem
```

Apply `rational_reconstruction` to each coefficient of $a$, resulting in either a fail (return (false, s.th.)) or (true, g) for some rational polynomial $g$ s.th. $g \equiv a \bmod M$.
