```
divexact(x::AbsMSeries{T}, y::AbsMSeries{T}; check::Bool=true) where T <: RingElement
```

系列 $x$ を系列 $y$ で割った正確な商を返します。この関数は現在、$y$ が可逆系列であると仮定しています。
