```julia
KineticEnergyDissipationRate(model; U, V, W, location)

```

Calculate the Kinetic Energy Dissipation Rate, defined as

```
ε = ν (∂uᵢ/∂xⱼ) (∂uᵢ/∂xⱼ)
ε = ∂ⱼuᵢ ⋅ Fᵢⱼ
```

where ∂ⱼuᵢ is the velocity gradient tensor and Fᵢⱼ is the stress tensor.
