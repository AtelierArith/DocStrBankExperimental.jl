```
residual_order_condition(t::ColoredRootedTree, ark::AdditiveRungeKuttaMethod)
```

順序条件の残差 `(Φ(t) - 1/γ(t)) / σ(t)` は、[`elementary_weight`](@ref) `Φ(t)`, [`density`](@ref) `γ(t)`, および [`symmetry`](@ref) `σ(t)` の [`AdditiveRungeKuttaMethod`](@ref) `ark` に対する、色付き根付き木 `t` のものです。

# 参考文献

  * A. L. Araujo, A. Murua, and J. M. Sanz-Serna. "Symplectic Methods Based on Decompositions". SIAM Journal on Numerical Analysis 34.5 (1997): 1926–1947. [DOI: 10.1137/S0036142995292128](https://doi.org/10.1137/S0036142995292128)
  * Butcher, John Charles. Numerical methods for ordinary differential equations. John Wiley & Sons, 2008. Section 312
