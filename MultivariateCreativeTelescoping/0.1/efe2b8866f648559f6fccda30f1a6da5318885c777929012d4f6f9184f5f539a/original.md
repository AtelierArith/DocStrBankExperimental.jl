```
irreducible_monomials(precomp ::RepInIntMod, l :: Int, A :: OreAlg)
```

Returns every monomial of degree up to l that do not have smaller representatives w.r.t the order of A  in the integral of the module defined in precomp. 

Warning: If the parameter sigma chosen for precomp is not large enough, this function may return some reducible monomials.
