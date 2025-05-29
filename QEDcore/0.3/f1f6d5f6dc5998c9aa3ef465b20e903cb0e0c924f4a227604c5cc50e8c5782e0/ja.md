```julia
MFourMomentum(t, x, y, z)

```

インターフェースは各数値のような入力を float64 に変換します:

```julia
MFourMomentum(
    t::Union{Integer, Irrational, Rational},
    x::Union{Integer, Irrational, Rational},
    y::Union{Integer, Irrational, Rational},
    z::Union{Integer, Irrational, Rational}
) -> QEDcore.MFourMomentum

```
