```
interpolate(S::PolyRing, x::Vector{T}, y::Vector{T}) where T <: RingElement
```

長さ $n$ が同じ2つの値の配列 $xs$ と $ys$ が与えられたとき、$f$ が多項式環 $R$ において長さが最大 $n$ であり、$f$ が点 $xs$ で値 $ys$ を持つ多項式を見つけます。配列 $xs$ と $ys$ の値は、多項式環 $R$ の基底環に属している必要があります。そのような多項式が存在しない場合、例外が発生します。
