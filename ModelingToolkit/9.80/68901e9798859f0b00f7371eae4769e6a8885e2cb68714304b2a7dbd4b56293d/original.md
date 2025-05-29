```
change_independent_variable(
    sys::AbstractODESystem, iv, eqs = [];
    add_old_diff = false, simplify = true, fold = false
)
```

Transform the independent variable (e.g. $t$) of the ODE system `sys` to a dependent variable `iv` (e.g. $u(t)$). The transformation is well-defined when the mapping between the new and old independent variables are one-to-one. This is satisfied if one is a strictly increasing function of the other (e.g. $du(t)/dt > 0$ or $du(t)/dt < 0$).

Any extra equations `eqs` involving the new and old independent variables will be taken into account in the transformation.

# Keyword arguments

  * `add_old_diff`: Whether to add a differential equation for the old independent variable in terms of the new one using the inverse function rule $dt/du = 1/(du/dt)$.
  * `simplify`: Whether expanded derivative expressions are simplified. This can give a tidier transformation.
  * `fold`: Whether internal substitutions will evaluate numerical expressions.

# Usage before structural simplification

The variable change must take place before structural simplification. In following calls to `structural_simplify`, consider passing `allow_symbolic = true` to avoid undesired constraint equations between between dummy variables.

# Usage with non-autonomous systems

If `sys` is non-autonomous (i.e. $t$ appears explicitly in its equations), consider passing an algebraic equation relating the new and old independent variables (e.g. $t = f(u(t))$). Otherwise the transformed system can be underdetermined. If an algebraic relation is not known, consider using `add_old_diff` instead.

# Usage with hierarchical systems

It is recommended that `iv` is a non-namespaced variable in `sys`. This means it can belong to the top-level system or be a variable in a subsystem declared with `GlobalScope`.

# Example

Consider a free fall with constant horizontal velocity. Physics naturally describes position as a function of time. By changing the independent variable, it can be reformulated for vertical position as a function of horizontal position:

```julia
julia> @variables x(t) y(t);

julia> @named M = ODESystem([D(D(y)) ~ -9.81, D(D(x)) ~ 0.0], t);

julia> M = change_independent_variable(M, x);

julia> M = structural_simplify(M; allow_symbolic = true);

julia> unknowns(M)
3-element Vector{SymbolicUtils.BasicSymbolic{Real}}:
 xˍt(x)
 y(x)
 yˍx(x)
```
