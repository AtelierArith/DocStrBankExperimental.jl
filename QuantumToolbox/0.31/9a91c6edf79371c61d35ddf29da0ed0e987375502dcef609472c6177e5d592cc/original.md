```
correlation_3op_1t(H::AbstractQuantumObject,
    ψ0::Union{Nothing,QuantumObject},
    τlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple},
    A::QuantumObject,
    B::QuantumObject,
    C::QuantumObject;
    kwargs...)
```

Returns the two-time correlation function (with only one time coordinate $\tau$) of three operators $\hat{A}$, $\hat{B}$ and $\hat{C}$: $\left\langle \hat{A}(0) \hat{B}(\tau) \hat{C}(0) \right\rangle$ for a given initial state $|\psi_0\rangle$.

If the initial state `ψ0` is given as `nothing`, then the [`steadystate`](@ref) will be used as the initial state. Note that this is only implemented if `H` is constant ([`QuantumObject`](@ref)).
