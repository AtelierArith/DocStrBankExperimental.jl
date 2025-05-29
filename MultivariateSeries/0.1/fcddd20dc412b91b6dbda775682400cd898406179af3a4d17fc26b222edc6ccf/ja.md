```
 *(v::Variable,   σ::Series{C,M}) -> Series{C,M}
 *(m::Monomial,   σ::Series{C,M}) -> Series{C,M}
 *(t::Term,       σ::Series{C,M}) -> Series{C,M}
 *(p::Polynomial, σ::Series{C,M}) -> Series{C,M}
```

多重積（または共積）では、変数が多項式内で反転され、正の指数を持つ単項式が系列に保持されます。
