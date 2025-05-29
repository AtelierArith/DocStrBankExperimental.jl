```
truncate(::AbstractPolynomial{T};
    rtol::Real = Base.rtoldefault(real(T)), atol::Real = 0)
```

ゼロに近い係数を `rtol` と `atol` によって決定されるように丸め、次に先頭のゼロを切り捨てます。新しい多項式を返します。
