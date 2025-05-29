`Frac(a::Mvp,b::Mvp;pol=false,prime=false)`

`Mvp`s  `a` and `b` are promoted to  same coefficient type, and checked for being  true polynomials  without common  monomial factor (unless `pol=true` asserts  that this  is already  the case)  and unless `prime=true` they are made prime to each other by dividing by their gcd.
