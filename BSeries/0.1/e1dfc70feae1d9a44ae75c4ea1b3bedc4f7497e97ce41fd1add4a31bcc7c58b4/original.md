```
evaluate(f, u, dt, series, reduce_order_by=0)
```

Evaluate the B-series `series` specialized to the ordinary differential equation $u'(t) = f(u(t))$ with vector field `f` and dependent variables `u` for a time step size `dt`.

Here, `u` is assumed to be a vector of symbolic variables and `f` is assumed to be a vector of expressions in these variables for plain B-series. For B-series with colored trees, `f` must be a tuple of vectors of expressions in the variables `u`. Currently, symbolic variables from

  * [SymEngine.jl](https://github.com/symengine/SymEngine.jl),
  * [SymPy.jl](https://github.com/JuliaPy/SymPy.jl), and
  * [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl)

are supported.

The powers of `dt` can be controlled by `reduce_order_by` to make them different from the usual `order(t)` for a rooted tree `t`. This can be useful in the context of [`modified_equation`](@ref)s or [`modifying_integrator`](@ref)s, where the B-series coefficients are those of $h fₕ$, i.e., they contain an additional power of `dt`. In this case, the B-series of the vector field can be obtained using `reduce_order_by = 1`.

# References

Section 3.2 of

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
