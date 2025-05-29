```
 *(v::Variable,   σ::Series{C,M}) -> Series{C,M}
 *(m::Monomial,   σ::Series{C,M}) -> Series{C,M}
 *(t::Term,       σ::Series{C,M}) -> Series{C,M}
 *(p::Polynomial, σ::Series{C,M}) -> Series{C,M}
```

The dual product (or co-product) where variables are inverted in the polynomial and the monomials with positive exponents are kept in the series.
