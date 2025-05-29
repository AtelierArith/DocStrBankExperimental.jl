```
prime_decomposition_nonindex(f::Map, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Z_K::AbsSimpleNumFieldOrder) -> Vector{Tuple{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}}
```

Given a map $f: k\to K$ of number fields defined over $\mathbb Q$ and a prime ideal in the maximal order of $k$, find all prime ideals in the maximal order of $K$ above. The ideals will belong to $Z_K$ which defaults to "the" maximal order of $K$.
