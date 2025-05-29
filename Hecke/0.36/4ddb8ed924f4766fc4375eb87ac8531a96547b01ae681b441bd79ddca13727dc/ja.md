```
characteristic_polynomial(f::Generic.Poly{T}, g::Generic.Poly{T}) where T <: Union{PadicFieldElem, QadicFieldElem} -> Generic.Poly{T}
```

$$
\mathrm{ResidueRingElem}_x(f(x), t- g(x))
$$

を計算します。
