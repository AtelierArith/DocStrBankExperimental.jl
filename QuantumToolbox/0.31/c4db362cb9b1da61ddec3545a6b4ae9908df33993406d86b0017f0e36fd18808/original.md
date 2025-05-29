```
liouvillian(H::AbstractQuantumObject, c_ops::Union{Nothing,AbstractVector,Tuple}=nothing, Id_cache=I(prod(H.dimensions)))
```

Construct the Liouvillian [`SuperOperator`](@ref) for a system Hamiltonian $\hat{H}$ and a set of collapse operators $\{\hat{C}_n\}_n$:

$$
\mathcal{L} [\cdot] = -i[\hat{H}, \cdot] + \sum_n \mathcal{D}(\hat{C}_n) [\cdot]
$$

where 

$$
\mathcal{D}(\hat{C}_n) [\cdot] = \hat{C}_n [\cdot] \hat{C}_n^\dagger - \frac{1}{2} \hat{C}_n^\dagger \hat{C}_n [\cdot] - \frac{1}{2} [\cdot] \hat{C}_n^\dagger \hat{C}_n
$$

The optional argument `Id_cache` can be used to pass a precomputed identity matrix. This can be useful when the same function is applied multiple times with a known Hilbert space dimension.

See also [`spre`](@ref), [`spost`](@ref), and [`lindblad_dissipator`](@ref).
