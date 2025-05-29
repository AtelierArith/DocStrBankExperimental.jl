```
function BasisDependence{StaircaseDependence}(
    is_dependent::Function,
    basis::MB.AbstractPolynomialBasis,
)
```

Computes the set of standard monomials using the *greedy sieve* algorithm presented in [LLR08, Algorithm 1]. A monomial outside of `basis` is assumed to be independent. Otherwise, if its index in `basis` is `i`, `is_dependent` returns whether it is dependent.

[LLR08] Lasserre, Jean Bernard and Laurent, Monique, and Rostalski, Philipp. *Semidefinite characterization and computation of zero-dimensional real radical ideals.* Foundations of Computational Mathematics 8 (2008): 607-647.
