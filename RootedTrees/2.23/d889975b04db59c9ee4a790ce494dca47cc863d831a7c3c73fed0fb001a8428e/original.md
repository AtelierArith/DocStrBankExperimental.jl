```
residual_order_condition(t::ColoredRootedTree, ark::AdditiveRungeKuttaMethod)
```

The residual of the order condition   `(Φ(t) - 1/γ(t)) / σ(t)` with [`elementary_weight`](@ref) `Φ(t)`, [`density`](@ref) `γ(t)`, and [`symmetry`](@ref) `σ(t)` of the [`AdditiveRungeKuttaMethod`](@ref) `ark` for the colored rooted tree `t`.

# References

  * A. L. Araujo, A. Murua, and J. M. Sanz-Serna. "Symplectic Methods Based on Decompositions". SIAM Journal on Numerical Analysis 34.5 (1997): 1926–1947. [DOI: 10.1137/S0036142995292128](https://doi.org/10.1137/S0036142995292128)
  * Butcher, John Charles. Numerical methods for ordinary differential equations. John Wiley & Sons, 2008. Section 312
