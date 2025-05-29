```
modifying_integrator(f, u, dt, series_integrator)
```

Compute the B-series of the [`modifying_integrator`](@ref) equation of the time integration method with B-series `series_integrator` with respect to the ordinary differential equation $u'(t) = f(u(t))$ with vector field `f` and dependent variables `u` for a time step size `dt`.

Here, `u` is assumed to be a vector of symbolic variables and `f` is assumed to be a vector of expressions in these variables for plain B-series. For B-series with colored trees, `f` must be a tuple of vectors of expressions in the variables `u`. Currently, symbolic variables from

  * [SymEngine.jl](https://github.com/symengine/SymEngine.jl),
  * [SymPy.jl](https://github.com/JuliaPy/SymPy.jl), and
  * [Symbolics.jl](https://github.com/JuliaSymbolics/Symbolics.jl)

are supported.
