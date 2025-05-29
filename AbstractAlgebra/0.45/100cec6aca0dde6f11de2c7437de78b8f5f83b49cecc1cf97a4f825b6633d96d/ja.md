```
polynomial_to_power_sums(f::PolyRingElem{T}, n::Int=degree(f)) where T <: RingElement -> Vector{T}
```

ニュートン（またはニュートン-ジラール）公式を使用して、$f$の係数から$f$の根の最初の$n$個の累乗和を計算します。最初は根の（1次の）累乗の和から始まります。入力多項式は単位的で、少なくとも1次以上であり、定数項がゼロであってはなりません。
