```
A = LinearMapAA(f::Function, fc::Function, D::Dims{2} [, prop::NamedTuple)]
; T::Type = Float32, idim::Dims, odim::Dims)
```

Constructor given forward `f` and adjoint function `fc`.
