```
R,S,T = rstd(BPLUS,BMINUS,A,BM1,AM,AO,AR,AS)
R,S,T = rstd(BPLUS,BMINUS,A,BM1,AM,AO,AR)
R,S,T = rstd(BPLUS,BMINUS,A,BM1,AM,AO)
```

Polynomial synthesis in discrete time.

Polynomial synthesis according to "Computer-Controlled Systems" ch 10 to design a controller $R(q) u(k) = T(q) r(k) - S(q) y(k)$

Inputs:

  * `BPLUS`  : Part of open loop numerator
  * `BMINUS` : Part of open loop numerator
  * `A`      : Open loop denominator
  * `BM1`    : Additional zeros
  * `AM`     : Closed loop denominator
  * `AO`     : Observer polynomial
  * `AR`     : Pre-specified factor of R,

e.g integral part [1, -1]^k

  * `AS`     : Pre-specified factor of S,

e.g notch filter [1, 0, w^2]

Outputs: `R,S,T`  : Polynomials in controller

See function `dab` how the solution to the Diophantine- Aryabhatta-Bezout identity is chosen.

See Computer-Controlled Systems: Theory and Design, Third Edition Karl Johan Åström, Björn Wittenmark
