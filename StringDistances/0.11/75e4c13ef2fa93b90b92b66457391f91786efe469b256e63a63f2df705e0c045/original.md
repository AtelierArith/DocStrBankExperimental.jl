```
NMD(q::Int)
NMD(q::Int)
```

Creates a NMD (Normalized Multiset Distance) as introduced by Besiris and Zigouris 2013. The goal with this distance is to behave similarly to a normalized compression distance without having to do any actual compression (and thus being faster to compute).

The distance corresponds to

$(sum(max.(m(s1), m(s2)) - min(M(s1), M(s2))) / max(M(s1), M(s2))$

where $m(s)$ is the vector of q-gram counts for string $s$ and $M(s)$ is the sum of those counts.

For details see: https://www.sciencedirect.com/science/article/pii/S1047320313001417
