```
characteristic_polynomial(f::Generic.Poly{T}, g::Generic.Poly{T}) where T <: Union{PadicFieldElem, QadicFieldElem} -> Generic.Poly{T}
```

Computes $\mathrm{ResidueRingElem}_x(f(x), t- g(x))$.
