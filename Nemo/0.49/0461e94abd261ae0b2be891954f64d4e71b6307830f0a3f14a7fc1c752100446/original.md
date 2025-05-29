```
root_of_unity_as_args(a::QQBarFieldElem)
```

Return a pair of integers `(q, p)` such that the given `a` equals $e^{2 \pi i p / q}$. The denominator `q` will be minimal, with $0 \le p < q$. Throws if `a` is not a root of unity.
