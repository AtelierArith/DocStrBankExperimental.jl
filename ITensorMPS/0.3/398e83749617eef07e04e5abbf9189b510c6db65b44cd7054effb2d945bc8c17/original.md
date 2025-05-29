```
@preserve_ortho
```

Specify that a block of code preserves the orthogonality limits of an MPS/MPO that is being modified in-place. The first input is either a single MPS/MPO or a tuple of the MPS/MPO whose orthogonality limits should be preserved.

# Examples

```julia
s = siteinds("S=1/2", 4)

# Make random MPS with bond dimension 2
ψ₁ = random_mps(s, "↑"; linkdims=2)
ψ₂ = random_mps(s, "↑"; linkdims=2)
ψ₁ = orthogonalize(ψ₁, 1)
ψ₂ = orthogonalize(ψ₂, 1)

# ortho_lims(ψ₁) = 1:1
@show ortho_lims(ψ₁)

# ortho_lims(ψ₂) = 1:1
@show ortho_lims(ψ₂)

@preserve_ortho (ψ₁, ψ₂) begin
  ψ₁ .= addtags.(ψ₁, "x₁"; tags = "Link")
  ψ₂ .= addtags.(ψ₂, "x₂"; tags = "Link")
end

# ortho_lims(ψ₁) = 1:1
@show ortho_lims(ψ₁)

# ortho_lims(ψ₂) = 1:1
@show ortho_lims(ψ₂)
```
