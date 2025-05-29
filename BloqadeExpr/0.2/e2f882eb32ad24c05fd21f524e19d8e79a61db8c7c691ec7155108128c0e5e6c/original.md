```
rydberg_h(atoms; [C=2π * 862690 * MHz*µm^6], Ω[, ϕ, Δ])
```

Create a rydberg hamiltonian

$$
∑ \frac{C}{|x_i - x_j|^6} n_i n_j + \frac{Ω}{2} σ_x - Δ σ_n
$$

shorthand for

```julia
RydInteract(C, atoms) + SumOfXPhase(length(atoms), Ω, ϕ) - SumOfN(length(atoms), Δ)
```

# Arguments

  * `atoms`: a collection of atom positions.

# Keyword Arguments

  * `C`: optional, default unit is `MHz*µm^6`, interation parameter,   see also [`RydInteract`](@ref).
  * `Ω`: optional, default unit is `MHz`, Rabi frequencies, divided by 2, see also [`SumOfX`](@ref).
  * `Δ`: optional, default unit is `MHz`, detuning parameter, see [`SumOfN`](@ref).
  * `ϕ`: optional, does not have unit, the phase, see [`SumOfXPhase`](@ref).

!!! tips
    The rabi frequencies are divided by two in the Rydberg hamiltonian unlike directly constructing via [`SumOfX`](@ref) or [`SumOfXPhase`](@ref).


!!! tips
    The parameters of Hamiltonian have their own default units to match hardware, one can use [`Unitful.jl`](https://github.com/PainterQubits/Unitful.jl) to specify their units explicitly. If the units are specified explicitly, they will be converted to default units automatically.


# Example

```julia-repl
julia> using Bloqade

julia> atoms = [(1, ), (2, ), (3, ), (4, )]
4-element Vector{Tuple{Int64}}:
 (1,)
 (2,)
 (3,)
 (4,)

julia> rydberg_h(atoms)
∑ 5.42e6/|x_i-x_j|^6 n_i n_j
```

```julia-repl
julia> rydberg_h(atoms; Ω=0.1)
nqubits: 4
+
├─ ∑ 5.42e6/|x_i-x_j|^6 n_i n_j
└─ 0.05 ⋅ ∑ σ^x_i
```
