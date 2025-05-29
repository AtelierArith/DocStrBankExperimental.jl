```
CoulombDerivative(D, Z, ℓ)
```

Helper operator wrapping the `Derivative` operator in the case of a Coulomb potential of charge `Z` and centrifugal potential $ℓ(ℓ+1)/2r²$. Its main use is to correctly apply boundary conditions at $r=0$, when materializing derivatives.
