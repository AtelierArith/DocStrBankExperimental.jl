```
induce_rational_reconstruction(a::Generic.Poly{AbsSimpleNumFieldElem}, M::ZZRingElem) -> bool, Generic.Poly{AbsSimpleNumFieldElem}
```

Apply rational reconstruction to the coefficients of $a$. Implicitly assumes the coefficients to be integral (no checks done) returns true iff this is successful for all coefficients.
