```
power_sums_to_polynomial(P::Vector{T};
                 parent::PolyRing{T}=PolyRing(parent(P[1])) where T <: RingElement -> PolyRingElem{T}
```

与えられた根の累乗の和を用いて多項式を取得するために、ニュートン（またはニュートン-ジラール）同値を使用します。リストは空であってはならず、$f$が回復される多項式である場合、`degree(f)`のエントリを含む必要があります。リストは根の最初の累乗の和から始まる必要があります。
