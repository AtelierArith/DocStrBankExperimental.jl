```
evolve!(svs::StateVectorSimulator{T, S<:AbstractVector{T}}, operations::Vector{Instruction}) -> StateVectorSimulator{T, S}
```

Apply each operation of `operations` in-place to the state vector contained in `svs`.

Effectively, perform the operation:

$\left| \psi \right\rangle \to \hat{A} \left| \psi \right\rangle$

for each operation $\hat{A}$ in `operations`.
