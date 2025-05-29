`Frac(a::Pol,b::Pol;prime=false)

Polynomials  `a` and `b` are promoted to same coefficient type, and checked for  being true polynomials (otherwise they are both multiplied by the same power  of  the  variable  so  they  become  true  polynomials),  and unless `prime=true` they are checked for having a non-trivial `gcd`.
