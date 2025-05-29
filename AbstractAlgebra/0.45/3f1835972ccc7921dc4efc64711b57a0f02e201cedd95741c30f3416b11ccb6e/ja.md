```
to_univariate(R::PolyRing{T}, p::MPolyRingElem{T}) where T <: RingElement
```

多項式 $p$ が実際には単変数多項式であると仮定し、与えられた単変数多項式環 $R$ において多項式を単変数多項式に変換します。多項式 $p$ が複数の変数を含む場合は例外が発生します。
