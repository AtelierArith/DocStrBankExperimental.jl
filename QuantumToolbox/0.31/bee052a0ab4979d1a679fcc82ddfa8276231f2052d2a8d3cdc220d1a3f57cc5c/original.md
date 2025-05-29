```
correlation_3op_2t(H::AbstractQuantumObject,
    ψ0::Union{Nothing,QuantumObject},
    tlist::AbstractVector,
    τlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple},
    A::QuantumObject,
    B::QuantumObject,
    C::QuantumObject;
    kwargs...)
```

Returns the two-times correlation function of three operators $\hat{A}$, $\hat{B}$ and $\hat{C}$: $\left\langle \hat{A}(t) \hat{B}(t + \tau) \hat{C}(t) \right\rangle$ for a given initial state $|\psi_0\rangle$.

If the initial state `ψ0` is given as `nothing`, then the [`steadystate`](@ref) will be used as the initial state. Note that this is only implemented if `H` is constant ([`QuantumObject`](@ref)).
