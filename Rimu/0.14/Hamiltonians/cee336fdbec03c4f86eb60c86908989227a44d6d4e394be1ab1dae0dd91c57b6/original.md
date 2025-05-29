```
StringCorrelator(d::Int; address=nothing, type=nothing) <: AbstractOperator{T}
```

Operator for extracting string correlation between lattice sites on a one-dimensional Hubbard lattice separated by a distance `d` with `0 ≤ d < M`

$$
    Ĉ_{\text{string}}(d) = \frac{1}{M} \sum_{j}^{M} δ n̂_j
                                         (e^{i π \sum_{j ≤ k < j + d} δ n̂_k}) δ n̂_{j+d}
$$

Here, $δ n̂_j = n̂_j - n̄$ is the boson number deviation from the mean filling number and $n̄ = N/M$ is the mean filling number of lattice sites with $N$ particles and $M$ lattice sites (or modes).

Assumes a one-dimensional lattice with periodic boundary conditions. For usage see [`SuperfluidCorrelator`](@ref) and [`AllOverlaps`](@ref).

The default element type `T` is `ComplexF64`. This can be overridden with the `type` keyword argument. If an `address` is provided, then `T` is calculated from the address type. It is set to `ComplexF64` for non-integer filling numbers, and to `Float64` for integer filling numbers or if `d==0`.

See also [`HubbardReal1D`](@ref), [`G2RealCorrelator`](@ref), [`SuperfluidCorrelator`](@ref), [`AbstractOperator`](@ref), and [`AllOverlaps`](@ref).
