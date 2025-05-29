```
get_measurement_probabilities(x::Ket{Complex{T}},
    [target_bodies::Vector{U},
    hspace_size_per_body::Union{U,Vector{U}}=2])::AbstractVector{T}
    where {T<:Real, U<:Integer}
```

Returns a vector listing the measurement probabilities of the `target_bodies` of `Ket` `x`.

The Hilbert space size per body can be specified by providing a `Vector` of `Integer` for the `hspace_size_per_body` argument. The `Vector` must specify the Hilbert space size for each body. If the space size is uniform, a single `Integer` can be given instead. If only `x` is provided, the probabilities are provided for all the bodies.

The measurement probabilities are listed from the smallest to the largest computational basis state. For instance, for a 2-qubit `Ket`, the probabilities are listed for $\left|00\right\rangle$,  $\left|10\right\rangle$, $\left|01\right\rangle$, and $\left|11\right\rangle$. 

!!! note
    By convention, qubit 1 is the leftmost bit, followed by every subsequent qubit.  $\left|10\right\rangle$ has qubit 1 in state $\left|1\right\rangle$ and qubit 2 in state $\left|0\right\rangle$


# Examples

The following example constructs a `Ket`, where the probability of measuring  $\left|00\right\rangle$ is 50% and the probability of measuring $\left|01\right\rangle$ is also 50%.

```jldoctest get_measurement_probabilities
julia> ψ = 1/sqrt(2) * Ket([1, 0, 1, 0])
4-element Ket{ComplexF64}:
0.7071067811865475 + 0.0im
0.0 + 0.0im
0.7071067811865475 + 0.0im
0.0 + 0.0im


julia> get_measurement_probabilities(ψ)
4-element Vector{Float64}:
 0.4999999999999999
 0.0
 0.4999999999999999
 0.0

```

For the same `Ket`, the probability of measuring qubit 2 and finding 0 is 100%.

```jldoctest get_measurement_probabilities
julia> target_qubit = [2];

julia> get_measurement_probabilities(ψ, target_qubit)
2-element Vector{Float64}:
 0.9999999999999998
 0.0

```
