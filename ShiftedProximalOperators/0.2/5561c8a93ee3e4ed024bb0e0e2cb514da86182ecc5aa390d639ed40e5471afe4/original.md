```
shifted(h, x)
shifted(h, x, Δ, ρ)
```

Construct a shifted proximable function from a proximable function or from another shifted proximable function.

If `h` is a `ProximableFunction`, including a `ShiftedProximableFunction`, the form `shifted(h, x)` returns a `ShiftedProximableFunction` `ψ` such that `ψ(s) == h(x + s)`. Subsequently, `prox` may be called on `ψ`. The first form applies when `h` is a `ShiftedProximableFunction` and can be used to shift an already-shifted proximable function.

The form `shifted(h, x, Δ, ρ)` returns a `ShiftedProximableFunction` `ψ` such that `ψ(s) == h(x + s) + Ind({‖s‖ ≤ Δ})`, where `Ind(.)` represents the indicator of a set, in this case the indicator of a ball of radius `Δ`, in which the norm is defined by `ρ`.

### Arguments

  * `h::ProximableFunction` (including a `ShiftedProximableFunction`)
  * `x::AbstractVector`
  * `Δ::Real`
  * `ρ::ProximableFunction`.

Only certain combinations of `h` and `ρ` are supported; those for which the analytical form of the proximal operator is known.

If `h` is a shifted proximable function obtained from a previous call to `shifted()`, only the form `shifted(h, x)` is supported. If applicable, the resulting shifted proximable function is associated with the same `Δ` and `ρ` as `h`.

See the documentation of ProximalOperators.jl for more information.
