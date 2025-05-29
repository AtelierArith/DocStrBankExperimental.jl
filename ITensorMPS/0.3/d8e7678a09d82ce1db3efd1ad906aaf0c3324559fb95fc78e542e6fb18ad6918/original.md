```
apply(As::Vector{<:ITensor}, M::Union{MPS, MPO}; kwargs...)
product([...])
```

Apply the ITensors `As` to the MPS or MPO `M`, treating them as gates or matrices from pairs of prime or unprimed indices.

# Keywords

  * `cutoff::Real`: singular value truncation cutoff.
  * `maxdim::Int`: maximum MPS/MPO dimension.
  * `apply_dag::Bool = false`: apply the gate and the dagger of the gate (only relevant for MPO evolution).
  * `move_sites_back::Bool = true`: after the ITensor is applied to the MPS or  MPO, move the sites of the MPS or MPO back to their original locations.

# Examples

Apply one-site gates to an MPS:

```julia
N = 3

ITensors.op(::OpName"σx", ::SiteType"S=1/2", s::Index) =
  2*op("Sx", s)

ITensors.op(::OpName"σz", ::SiteType"S=1/2", s::Index) =
  2*op("Sz", s)

# Make the operator list.
os = [("σx", n) for n in 1:N]
append!(os, [("σz", n) for n in 1:N])

@show os

s = siteinds("S=1/2", N)
gates = ops(os, s)

# Starting state |↑↑↑⟩
ψ0 = MPS(s, "↑")

# Apply the gates.
ψ = apply(gates, ψ0; cutoff = 1e-15)

# Test against exact (full) wavefunction
prodψ = apply(gates, prod(ψ0))
@show prod(ψ) ≈ prodψ

# The result is:
# σz₃ σz₂ σz₁ σx₃ σx₂ σx₁ |↑↑↑⟩ = -|↓↓↓⟩
@show inner(ψ, MPS(s, "↓")) == -1
```

Apply nonlocal two-site gates and one-site gates to an MPS:

```julia
# 2-site gate
function ITensors.op(::OpName"CX", ::SiteType"S=1/2", s1::Index, s2::Index)
  mat = [1 0 0 0
         0 1 0 0
         0 0 0 1
         0 0 1 0]
  return itensor(mat, s2', s1', s2, s1)
end

os = [("CX", 1, 3), ("σz", 3)]

@show os

# Start with the state |↓↑↑⟩
ψ0 = MPS(s, n -> n == 1 ? "↓" : "↑")

# The result is:
# σz₃ CX₁₃ |↓↑↑⟩ = -|↓↑↓⟩
ψ = apply(ops(os, s), ψ0; cutoff = 1e-15)
@show inner(ψ, MPS(s, n -> n == 1 || n == 3 ? "↓" : "↑")) == -1
```

Perform TEBD-like time evolution:

```julia
# Define the nearest neighbor term `S⋅S` for the Heisenberg model
function ITensors.op(::OpName"expS⋅S", ::SiteType"S=1/2",
                     s1::Index, s2::Index; τ::Number)
  O = 0.5 * op("S+", s1) * op("S-", s2) +
      0.5 * op("S-", s1) * op("S+", s2) +
            op("Sz", s1) * op("Sz", s2)
  return exp(τ * O)
end

τ = -0.1im
os = [("expS⋅S", (1, 2), (τ = τ,)),
      ("expS⋅S", (2, 3), (τ = τ,))]
ψ0 = MPS(s, n -> n == 1 ? "↓" : "↑")
expτH = ops(os, s)
ψτ = apply(expτH, ψ0)
```
