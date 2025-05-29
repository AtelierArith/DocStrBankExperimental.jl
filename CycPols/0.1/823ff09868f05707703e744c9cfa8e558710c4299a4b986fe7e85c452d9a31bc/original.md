`CycPol`s are internally a `struct` with fields:

`.coeff`:  a coefficient, usually a `Cyc` or a `Pol`. The `Pol` case allows    to represent as `CycPol`s arbitrary `Pol`s which is useful sometimes.

`.valuation`: an `Int`.

`.v`: a ModuleElt{Rational{Int},Int} where pairs `r=>m` give the multiplicity `m` of `Root1(;r=r)` as a root.

So `CycPol(coeff,val,v)` represents `coeff*q^val*prod((q-Root1(;r=r))^m for (r,m) in v)`.
