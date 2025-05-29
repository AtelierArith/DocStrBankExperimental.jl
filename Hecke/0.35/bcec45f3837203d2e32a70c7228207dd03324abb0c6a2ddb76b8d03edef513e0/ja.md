```
induce_crt(a::ZZPolyRingElem, p::ZZRingElem, b::ZZPolyRingElem, q::ZZRingElem, signed::Bool = false) -> ZZPolyRingElem
```

整数多項式 $a$ と $b$ および互いに素な整数の剰余 $p$ と $q$ が与えられたとき、$f = a \bmod p$ および $f=b \bmod q$ を求めます。`signed` が設定されている場合は対称代表が使用され、そうでない場合は正のものが使用されます。
