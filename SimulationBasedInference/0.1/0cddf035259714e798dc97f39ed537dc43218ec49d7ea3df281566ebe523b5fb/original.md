```
unconstrained_forward_map(prior::AbstractSimulatorPrior, ζ)
```

Applies the forward map from unconstrained to forward model parameter `(g ∘ f): Ζ ↦ Θ ↦ Φ` where `f⁻¹` is the inverse bijector of `prior` (i.e. mapping from unconstrained Ζ to constrained Θ space) and `g` is defined by `forward_map` which maps from Θ to the parameter space of the forward model, Φ.
