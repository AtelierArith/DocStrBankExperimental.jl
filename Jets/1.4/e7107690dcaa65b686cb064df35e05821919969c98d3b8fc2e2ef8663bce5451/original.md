```
Jet(;dom, rng, f!, df!, df′!, upstate!, s)
```

Return a `Jet` with domain `dom::JetAbstractSpace`, range `rng::JetSAbstractpace`, with forward mapping  `f!::Function`, linearized forward mapping `df!::Function`, linearized adjoint mapping `df′!::Function`, Jacobian state modification function `upstate!::Function`, and state `s::NamedTuple`.

A jet describes a function `f!` and its linearization (forward `df!, and adjoint`df′!``) about a point.

If one of `f!` or `df!` is specified, and `df′!` is not, then we assume that `f!=df!=df′!`. This means that the operator is linear and self-adjoint.

If `f!` and `df!` are sepecified, bug `df′!` is not, then we assume that `df′!=df!`.  This means that the operator is nonlinear and self-adjoint.

# Example

Consider a nonlinear mapping with a self-adjoint linearization $f(x)=x^2$

```julia
using Jets
g!(m) = m.^2
dg!(δm; mₒ) = @. 2*mₒ*δm
jet = Jet(;dom=JetSpace(Float64,2), rng=JetSpace(Float64,2), f! = g!, df! = dg!)
```
