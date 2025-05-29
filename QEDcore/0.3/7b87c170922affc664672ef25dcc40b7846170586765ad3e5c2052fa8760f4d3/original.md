```julia
SFourMomentum(t, x, y, z)

```

The interface transforms each number-like input to float64:

```julia
SFourMomentum(
    t::Union{Integer, Irrational, Rational},
    x::Union{Integer, Irrational, Rational},
    y::Union{Integer, Irrational, Rational},
    z::Union{Integer, Irrational, Rational}
) -> QEDcore.SFourMomentum

```
