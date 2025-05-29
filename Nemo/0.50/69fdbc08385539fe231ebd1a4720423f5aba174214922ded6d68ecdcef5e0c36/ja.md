```
cos_minpoly(n::Int, x::ZZPolyRingElem)
```

$$
2 \cos(2 \pi / n)
$$

の最小多項式を返します。適切な$n$の選択により、これは任意の有理数$a$に対する$2 \cos(a \pi)$または$2 \sin(a \pi)$の最小多項式を与えます。
