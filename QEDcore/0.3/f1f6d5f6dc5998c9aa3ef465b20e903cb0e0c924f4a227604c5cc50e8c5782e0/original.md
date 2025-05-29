```julia
MFourMomentum(t, x, y, z)

```

The interface transforms each number-like input to float64:

```julia
MFourMomentum(
    t::Union{Integer, Irrational, Rational},
    x::Union{Integer, Irrational, Rational},
    y::Union{Integer, Irrational, Rational},
    z::Union{Integer, Irrational, Rational}
) -> QEDcore.MFourMomentum

```
