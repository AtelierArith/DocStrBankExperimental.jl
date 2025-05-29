```julia
struct NaiveInvert <: MPSKit.DDMRG_Flavour
```

An alternative approach to the dynamical DMRG algorithm, without quadratic terms but with a less controlled approximation. This algorithm minimizes the following cost function

$$
⟨ψ|(H - E)|ψ⟩ - ⟨ψ|ψ₀⟩ - ⟨ψ₀|ψ⟩
$$

which is equivalent to the original approach if

$$
|ψ₀⟩ = (H - E)|ψ⟩
$$

See also [`Jeckelmann`](@ref) for the original approach.
