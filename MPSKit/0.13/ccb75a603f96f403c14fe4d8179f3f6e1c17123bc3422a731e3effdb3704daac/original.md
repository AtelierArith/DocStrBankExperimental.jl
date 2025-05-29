```julia
struct FiniteExcited{A} <: MPSKit.Algorithm
```

Variational optimization algorithm for excitations of finite MPS by minimizing the energy of

$$
H - λᵢ |ψᵢ⟩⟨ψᵢ|
$$

## Fields

  * `gsalg::Any`: optimization algorithm
  * `weight::Float64`: energy penalty for enforcing orthogonality with previous states
