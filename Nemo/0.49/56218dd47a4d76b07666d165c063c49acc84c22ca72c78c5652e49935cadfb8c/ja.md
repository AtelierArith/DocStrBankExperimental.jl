```
divisor_lenstra(n::ZZRingElem, r::ZZRingElem, m::ZZRingElem)
```

もし $n$ が $0 < r < m < n$ の範囲で $r (\mod m)$ にある因子を持つ場合、この関数はその因子を返します。そうでない場合は $0$ を返します。これは $m$ が $n$ の立方根以上である場合にのみ効率的です。gcd$(r, m) = 1$ を要求し、この条件はチェックされません。
