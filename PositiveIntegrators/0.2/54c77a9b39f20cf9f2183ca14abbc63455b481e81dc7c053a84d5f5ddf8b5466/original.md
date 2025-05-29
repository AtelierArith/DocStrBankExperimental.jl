```
PDSProblem(P, D, u0, tspan, p = NullParameters();
           p_prototype = nothing,
           analytic = nothing,
           std_rhs = nothing)
```

A structure describing a system of ordinary differential equations in form of a production-destruction system (PDS). `P` denotes the function defining the production matrix $P$. The diagonal of $P$ contains production terms without destruction counterparts. `D` is the function defining the vector of destruction terms $D$ without production counterparts. `u0` is the vector of initial conditions and `tspan` the time span `(t_initial, t_final)` of the problem. The optional argument `p` can be used to pass additional parameters to the functions `P` and `D`.

The functions `P` and `D` can be used either in the out-of-place form with signature `production_terms = P(u, p, t)` or the in-place form `P(production_terms, u, p, t)`.

### Keyword arguments:

  * `p_prototype`: If `P` is given in in-place form, `p_prototype` or copies thereof are used to store evaluations of `P`. If `p_prototype` is not specified explicitly and `P` is in-place, then `p_prototype` will be internally set to `zeros(eltype(u0), (length(u0), length(u0)))`.
  * `analytic`: The analytic solution of a PDS must be given in the form `f(u0,p,t)`. Specifying the analytic solution can be useful for plotting and convergence tests.
  * `std_rhs`: The standard ODE right-hand side evaluation function callable as `du = std_rhs(u, p, t)` for the out-of-place form and as `std_rhs(du, u, p, t)` for the in-place form. Solvers that do not rely on the production-destruction representation of the ODE, will use this function instead to compute the solution. If not specified, a default implementation calling `P` and `D` is used.

## References

  * Hans Burchard, Eric Deleersnijder, and Andreas Meister. "A high-order conservative Patankar-type discretisation for stiff systems of production-destruction equations." Applied Numerical Mathematics 47.1 (2003): 1-30. [DOI: 10.1016/S0168-9274(03)00101-6](https://doi.org/10.1016/S0168-9274(03)00101-6)
