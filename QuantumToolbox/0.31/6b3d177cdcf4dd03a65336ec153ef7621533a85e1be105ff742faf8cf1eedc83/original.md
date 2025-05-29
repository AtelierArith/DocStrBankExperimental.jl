```
correlation_2op_1t(H::AbstractQuantumObject,
    ψ0::Union{Nothing,QuantumObject},
    τlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple},
    A::QuantumObject,
    B::QuantumObject;
    reverse::Bool=false,
    kwargs...)
```

Returns the two-time correlation function (with only one time coordinate $\tau$) of two operators $\hat{A}$ and $\hat{B}$ : $\left\langle \hat{A}(\tau) \hat{B}(0) \right\rangle$ for a given initial state $|\psi_0\rangle$.

If the initial state `ψ0` is given as `nothing`, then the [`steadystate`](@ref) will be used as the initial state. Note that this is only implemented if `H` is constant ([`QuantumObject`](@ref)).

When `reverse=true`, the correlation function is calculated as $\left\langle \hat{A}(0) \hat{B}(\tau) \right\rangle$.
